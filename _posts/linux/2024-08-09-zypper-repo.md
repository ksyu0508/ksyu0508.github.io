---
layout: post
title: zypper에서 패키지 설치 시 오류
subtitle: \'tmux\' not found in package names. Trying capabilities...
categories: [linux]
tags: [linux, tmux, zypper]
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

zypper에서 tmux를 설치할 떄에

``` bash
'tmux' not found in package names. Trying capabilities.
No provider of 'tmux' found.
Resolving package dependencies...

Nothing to do.
```

라는 메세지와 함께 설치가 안되는 상황이 발생하였다. 이 경우는 zypper의 레퍼지토리 설정이 제대로 되어있지 않아서 그런 것이다.

`zypper lr` 명령어를 통해서 현재 설치된 레퍼지토리 리스트를 확인할 수 있는다. 오류가 나는 경우, 이 명령어를 통해서 확인해본다면 `openSUSE Oss`, `openSUSE Non-Oss`, `openSUSE Update`등의 레퍼지토리가 비어있는 모습을 확인할 수 있을 것이다.

이 경우에는, 사용자가 직접 zypper에 레퍼지토리를 추가하여야 한다. 아래 명령어를 통해서 레퍼지토리를 추가할 수 있다

``` bash
# 레퍼지토리 추가
sudo zypper addrepo http://download.opensuse.org/distribution/leap/15.4/repo/oss/ openSUSE-Leap-15.4-Oss

sudo zypper addrepo http://download.opensuse.org/distribution/leap/15.4/repo/non-oss/ openSUSE-Leap-15.4-Non-Oss
```

``` bash
# 레퍼지토리 갱신
sudo zypper refresh
```

>>>키를 거부(r)하시겠습니까, 아니면 임시로 신뢰(t)하거나 항상 신뢰(a)하시겠습니까? [r/t/a/?] (r):
등의 메세지가 나오면 항상 신뢰를 선택한 후에 진행하면 된다.

위 명령어를 실행하고 나서 다시 원하는 패키지를 설치한다면 정상적으로 설치되는 모습을 확인할 수 있다. zypper을 처음 사용해보기 때문에, zypper의 문제인지, 내 서버 환경 자체의 문제인지는 정확하기는 모르겠지만, apt가 그립습니다...