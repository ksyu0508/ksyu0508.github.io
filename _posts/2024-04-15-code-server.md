---
layout: post
title: code-server 설치 및 HTTPS 연결 설정
subtitle: OMV에 code-server 설치하기
categories: [linux]
tags: [linux, NAS, code-server, OMV, self signed certificate, HTTPS]
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

![](https://drive.google.com/thumbnail?id=198zNVvvwQ9so5oD5FKotP3I9GIFPSB2j&sz=w1000)

안드로이드 크롬 메뉴의 홈화면 내보내기 기능을 이용해서, 컴퓨터의 크로니움 기반 브라우저에서 웹을 어플리케이션으로 설치할 수 있는 것처럼 code-server를 별도의 어플처럼 사용할 수 있다. 웹 브라우저에서 접속할 경우에 단축키가 웹 브라우저와 code-server의 것이 섞이기 때문에 사용하기가 불편하다.

![](https://drive.google.com/thumbnail?id=1CG1QC2WU1SLQgNEXeMlq97juuOlrFATs&sz=w1000)
*<center>갤럭시탭 S8에서 실행 중인 code-server 모습</center>*


## Self signed certificate를 활용한 HTTPS 구성

![](https://drive.google.com/thumbnail?id=191FCd0K_x--FM_hqSsypDaeU-uQx6Amr&sz=w1000)

code-server의 경우 기본적으로는 HTTP를 이용해서 연결되는데, vpn을 활용하고 있어서 내부망으로만 접속할 예정이기에 따로 HTTPS를 설정하지 않으려 하였지만, HTTPS 연결이 아닌 HTTP로만 연결 시 제대로 작동하지 않을 수 있다는 경고가 친절하게 나온다. 그냥 사용하려 했지만, 클립보드를 비롯하여 마크다운 프리뷰 기능이 작동하지 않기 때문에 결국 HTTPS를 구성하기로 하였다.


외부망에 노출되어 있는 상태는 아니였기에 따로 nginx proxy manager 등의 프록시를 활용한 HTTPS 구성은 진행하지 않고, 간단하게 self signed certificate를 이용하여 HTTPS를 구성하려고 하였다.

{% linkpreview "https://coder.com/docs/code-server/latest/guide#https-and-self-signed-certificates" %}

code-server documetation을 확인해보면 self-signed certificate를 활용하여 HTTPS를 구성할 수 있음을 안내하고 있다. 실행시 `--cert` 옵션을 추가하여 자동으로 인증서 발급 후 HTTPS 연결을 진행하거나, `--cert`와 `--cert-key`옵션에 따로 `.crt`와 `.key`파일 경로를 넣어서 별도로 발급한 인증서를 사용하여 HTTPS 연결을 진행할 수도 있다.

docker compose를 활용하여 code-server 이미지를 구동하고 있기 때문에, 인증서를 yaml 파일에 volumes와 command를 활용하여 추가하려 하였지만 제대로 작동하지 않았고, 결국 일단 컨테이너 실행 후 컨테이너 내부의 config 파일을 직접 변경하기로 하였다. `/config/.config/code-server/config.yaml`로 기본적으로 위치하고 있다.

```yaml
bind-addr: 127.0.0.1:8080
auth: password
password: # PASSWORD HASH
cert: true
```

여기서 `cert` 옵션 기본이 false로 되어 있는데, `true`로 변경 후 컨테이너를 재실행시키면 된다. 그러면 HTTPS로 접속이 되는 모습을 확인할 수 있다.

![](https://drive.google.com/thumbnail?id=199OM1mlbiEb4fQkpkiZZY6mzAkPwoNXk&sz=w500)
*<center>그렇지만 여전히 제일 중요한 markdwon preview 기능이 작동하지 않는다...</center>*

## 파이어폭스로 문제 임시 해결..

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/Mozilla_Firefox_logo_2013.svg/227px-Mozilla_Firefox_logo_2013.svg.png)
*<center>어떻게 우리는 코드 서버를 구동할 수 있었을까? 정답은 파이어폭스에 있었어</center>*


사실 code-server에서 HTTPS 구성을 해야지 제대로 사용할 수 있다는 내용은 쉽게 찾아 볼 수 있다. 대부분의 사람들은 nginx 등을 활용하여 프록시를 구성하고 SSL 인증서를 발급 후 HTTPS 연결을 만들어 준다. 하지만, 외부망에 연결하고 도메인에 연결하기에는 공유기, VM 등의 여러 조건이 맞물려서 구성하기 귀찮고, 또 혼자서 사용할 목적이다 보니 굳이 외부망에 노출하기 꺼려지기도 해서 self signed certificate로 구성하려 하였다. self signed certificate의 경우 크롬이나 엣지 등의 브라우저에서 연결 전에 안전하지 않은 연결이라고 친절하게 경고를 해주지만, 이를 무시하고 접속할 수 있다.

{% linkpreview "https://stackoverflow.com/questions/38728176/can-you-use-a-service-worker-with-a-self-signed-certificate" %}

위 스레드를 확인해본 결과, 강제로 연결을 진행하더라도 보안상의 이유로 완전히 모든 기능을 사용할 수 있게 해주는 것은 아닌 것을 확인할 수 있었고, Firefox 브라우저를 활용하여 접속하면 문제 없이 기능이 작동하는 모습을 보여준다. 아마 관련 보안 조치 적용이 크롬이나 엣지보다는 약한 이유 등으로 보여지지만 확실치는 않다.
안드로이드 태블릿이라는 조건 하에서 둘다 적용하기에는 애매하였는데, PC 환경이나 ipad 등의 경우 크롬에서 이 보안 관련 옵션을 끄고 브라우저로 접속하면 문제가 없다는 내용을 확인할 수 있다. 또, 디바이스나 브라우저에게 code-server에서 만든 인증서를 신뢰하도록 설정해주는 방법도 있다.  

![](https://drive.google.com/thumbnail?id=19E3GlCollq_liEAhKV9W-VeyN4KqVJmm&sz=w1000)

파이어폭스 브라우저 자체의 문제로, 한글 인코딩이 깨지거나, 폰트가 궁서체로 나오고, 홈화면에 추가 기능을 사용해도 단독 어플리케이션 처럼은 활용할 수 없다는 아쉬움이 존재한다. 그렇지만, 간단한 코딩이나 메모 용도로 사용하기에는 문제 없어보인다.