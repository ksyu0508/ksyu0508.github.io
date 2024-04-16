---
layout: post
title: omv-firstaid를 활용한 OMV 초기 설정 변경
subtitle: 관리자 비밀번호 초기화, webUI 포트 변경 등
categories: [linux]
tags: [linux, NAS, OMV, omv-firstaid]
published: False
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
