---
layout: post
title: code-server 설치 및 HTTPS 연결 설정
subtitle: OMV에 code-server 설치하기
categories: [linux]
tags: [linux, NAS, code-server, nginx, OMV, proxy, HTTPS]
published: True
# github blog template

# 1. 링크 넣기
# {% linkpreview "{링크 주소}" %}

# 2. 사진 넣기
# ![]({사진 주소})
# *<center>{사진 설명}</center>*

# 3. 줄 번호 있는 코드
# {% highlight {코드 종류} wl linenos %}
# {% endhighlight %}
---

## 서론

현재 인턴하고 있는 회사가 보안이 중요하여 사내망에서 작성된 문서나 코드를 밖으로 반출하기가 까다롭다. 개인 공부 내용 정리 및 테스트 개발 환경이 필요하지만 허용되는 개인 전자기기는 아이패드, 갤럭시탭 등의 태블릿까지만 허용되기 때문에, 태블릿에서 사용할 수 있는 간단한 개발환경을 만들고자 한다. 주피터 랩등의 환경도 있지만, 파이썬 뿐만 아니라 다른 파일들도 다룰 예정이기 때문에 익숙한 VS code와 같은 IDE를 원했는데, 놀랍게도 VS code는 마이크로소프트에서 만들었지만 오픈소스이기 때문에, code-server와 같은 웹으로 호스트할 수 있는 IDE가 만들어져 있다. 따라서 개인 NAS에 code-server를 설치하고 안드로이드 태블릿에서 사용할 계획을 세웠다.

{% linkpreview "https://github.com/microsoft/vscode" %}

## Code-Server 설치

{% linkpreview "https://hub.docker.com/r/linuxserver/code-server" %}

docker compose를 활용하여 코드 서버를 구성하였다. 서버의 경우 외부망 접속시 VPN을 활용하고 있기 때문에, 외부에 코드서버가 노출될 일이 없어서 편의를 위해서 별도로 비밀번호를 설정하지는 않았다. code-server의 경우 vs code처럼 터미널을 열 수 있기 때문에 외부에 포트 개방하는 경우에는 비밀번호 설정 이외에도 추가 보안 설정을 필요로 할 것이다.

``` YAML
services:
  code-server:
    image: lscr.io/linuxserver/code-server:latest
    container_name: code-server
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Asia/Seoul
    #   - PASSWORD=password #optional
    #   - HASHED_PASSWORD= #optional
    #   - SUDO_PASSWORD=password #optional
    #   - SUDO_PASSWORD_HASH= #optional
    #   - PROXY_DOMAIN=code-server.my.domain #optional
      - DEFAULT_WORKSPACE=/workspace
    volumes:
      - /path/to/appdata/config:/config
      - {마운트 할 디렉토리}:/workspace
    ports:
      - 8443:8443
    restart: unless-stopped
```

컨테이너로 구성된 코드서버로 접속 시, 파일 탐색은 컨테이너 내부만 가능하기 때문에 미리 사용하고자 할 디렉토리를 연결해주어야 한다. 도커 컴포즈 파일에서 DEFAULT_WORKSPACE를 설정할 수 있는데 이는 컨테이너 파일 시스템 기준이며, 여기에 원래 서버에서 사용하고자 할 디렉토리를 마운트한다면 편하게 code-server를 활용 수 있을 것이다.


안드로이드 크롬 메뉴의 홈화면 내보내기 기능을 이용해서, 컴퓨터의 크로니움 기반 브라우저에서 웹을 어플리케이션으로 설치할 수 있는 것처럼 code-server를 별도의 어플처럼 사용할 수 있다. 웹 브라우저에서 접속할 경우에 단축키가 웹 브라우저와 code-server의 것이 섞이기 때문에 사용하기가 불편하다. 엣지 브라우져는 컴퓨터에는 기능이 있는데 모바일에서는 왠지는 모르겠으나 찾을 수 없었다.

![](https://drive.google.com/thumbnail?id=1CG1QC2WU1SLQgNEXeMlq97juuOlrFATs&sz=w1000)
*<center>갤럭시탭 S8에서 실행 중인 code-server 모습</center>*

code-server의 경우 기본적으로는 HTTP를 이용해서 연결되는데, vpn을 활용하고 있어서 내부망으로만 접속할 예정이기에 따로 HTTPS를 설정하지 않으려 하였지만, HTTPS 연결이 아닌 HTTP로만 연결 시 제대로 작동하지 않을 수 있다는 경고가 친절하게 나온다. 그냥 사용하려 했지만, 마크다운 프리뷰 기능이 작동하지 않기 때문에 결국 HTTPS를 구성하기로 하였다.

## OMV 관리 페이지 포트 변경

OMV의 경우 기본적으로 관리 페이지가 80번 포트로 지정되어있기 때문에, 프록시 구성을 위해서는 80번과 443번 포트를 비워주어야 한다. 

```bash
~# omv-firstaid
```
OMV를 쉘로 접속한 후 `omv-firstaid`를 실행시켜주면 된다.(관리자 권한 필요) 실행 시 아래와 같은 모습을 확인할 수 있을 것이다. 만약 실행되지 않는다면 SSH가 아닌 직접 접속해야 할 것이다. OMV 관련 초기 설정을 변경할 수 있으며, 관리자 비밀번호 초기화, 관리자 접속 실패 잠금 해제 등의 메뉴들이 있는 모습을 확인할 수 있다.

![](https://drive.google.com/thumbnail?id=1HB2W44F46rkS6VihF-JiohIfPfgAbNeW&sz=w1000)

3번째 선택지를 확인해보면, `Configure Workbench`가 있다.

![](https://drive.google.com/thumbnail?id=1LfbkYrnEpLVLBtnZAJzCWXT9P3xp4JEO&sz=w1000)

선택해주면 아래와 같은 화면을 볼 수 있으며, 80번과 443번 포트가 아닌 임의의 포트로 변경하여 준다. HTTPS의 경우 변경해도 되지만 사용하지 않음으로 체크하고 일단 넘어가자.


## nginx를 활용한 프록시 서버 설치


```bash
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout ./self-signed.key -out ./self-signed.crt
```



