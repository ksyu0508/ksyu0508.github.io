---
layout: post
title: github blog 링크 미리보기 기능 추가
subtitle: jekyll-linkpreview plugin
categories: [github blog]
tags: [jekyll, open graph]
published: True
---

## 서론

github blog에서도 네이버 블로그나 티스토리 블로그에서 처럼 링크 임베딩시 링크 미리보기가 적용되었으면 해서 관련 플러그인을 찾아보았다. `jekyll-linkpreview`라는 플러그인이 있어 적용해보려 한다. github blog에서 기본 플러그인 이외의 플러그인을 사용하고 싶다면 다음 포스팅을 확인하면 도움이 될 것이다.

## jekyll-preview 설치

{% linkpreview "https://github.com/ysk24ok/jekyll-linkpreview" %}

### 1. `Gemfile`에 아래 내용 추가

```
gem 'jekyll-linkpreview', group: :jekyll_plugins

group :development do
    gem 'appraisal', git: 'https://github.com/thoughtbot/appraisal'
  end
```
### 2. 초기 설정
* `_cache` 디렉토리를 블로그 폴더 최상단에 생성
* [linkpreview.css](https://github.com/ysk24ok/jekyll-linkpreview/blob/master/assets/css/linkpreview.css)파일을 assets/css에 추가
* `linkpreview.css`가 적용될 수 있도록 `_include/head.html`에 스타일 시트 추가

``` html
<link rel="stylesheet" type="text/css" href="/assets/css/linkpreview.css" media="screen">
```

### 3. 설치

``` Ruby_prompt
$ bundle install
```

## linkpreview 사용법

마크다운 파일에 자신이 원하는 링크를 linkpreview 태그로 감싸기

``` Markdown
{% raw %}{% linkpreview "https://ogp.me/" %}{% endraw %}
````

실행결과:
{% linkpreview "https://ogp.me/" %}


## 사용자 정의 설정

`_includes`에 Open graph가 있는 페이지에 대해서는 `linkpreview.html`, Open graph가 없는 페이지에 대해서는 `linkpreview_nog.html`파일을 이용해 place holder를 사용한다면 원하는 형태로 링크 미리보기의 내용을 변경할 수 있다. 필자는 기본에서 딱히 변경한 것은 없고, h2태그를 사이드바가 제목으로 인식해버리는 문제가 있어서 태그만 변경해주었다. 태그의 목록은 마찬가지로 플러그인 [깃헙](https://github.com/ysk24ok/jekyll-linkpreview/tree/master#custom-templates)에서 확인이 가능하다. 다양한 태그가 있지만, 딱히 필요성을 느끼지는 못했다. 지금이 제일 깔끔...

{% highlight HTML wl linenos %}
<div class="jekyll-linkpreview-wrapper">
  <div class="jekyll-linkpreview-wrapper-inner">
    <div class="jekyll-linkpreview-content">
      <div class="jekyll-linkpreview-image">
        <a href="{{url}}" target="_blank">
          <img src="{{image}}" />
        </a>
      </div>

      <div class="jekyll-linkpreview-body">
        <h1 class="jekyll-linkpreview-title">
          <a href="{{url}}" target="_blank">{{title}}</a>
        </h1>
        <div class="jekyll-linkpreview-description">{{description}}</div>
      </div>
    </div>
    <div class="jekyll-linkpreview-footer">
      <a href="{{domain}}" target="_blank">{{domain}}</a>
    </div>
  </div>
</div>
{% endhighlight %}

`linkpreview.css`의 내용을 변경해서 미리보기의 모양을 변경할 수 있다. 아래의 코드는 기본코드에서 박스 그림자, 사진 위치 위로 크게 변경 등의 커스터마이징이 적용되었다.

{% highlight CSS wl linenos %}
.jekyll-linkpreview-wrapper {
  max-width: 600px;
  margin-bottom: 20px;
  background-color: #f8f8f8;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  overflow: visible;
  position: relative;
}

.jekyll-linkpreview-wrapper-inner {
  border: 1px solid rgba(0, 0, 0, 0.1);
  padding: 12px;
}

.jekyll-linkpreview-content {
  position: relative;
  margin-bottom: 10px;
  background-color: #f8f8f8;
  border-radius: 4px;
}

.jekyll-linkpreview-image {
  display: block;
  margin: 0 auto;
  max-width: 100%;
  height: auto;
  border-radius: 4px;
}

.jekyll-linkpreview-body {
  margin-top: 20px;
}

.jekyll-linkpreview-title {
  font-size: 17px;
  margin: 0 0 2px;
  line-height: 1.3;
}

.jekyll-linkpreview-description {
  line-height: 1.5;
  font-size: 13px;
}

.jekyll-linkpreview-footer {
  font-size: 11px;
}

{% endhighlight %}


## Open Graph란?

`Open Graph`는 웹 페이지의 메타데이터를 정의하는 프로토콜이다. 이 메타데이터는 웹 페이지가 SNS와 같은 소셜 그래프에서 공유될 때 제목, 설명, 이미지 등과 같은 정보를 제공한다. 일반적으로 우리가 SNS 사용 시 접하는 사진을 포함한 미리보기가 바로 이것이며, 웹 페이지를 소셜 미디어에서 보다 풍부하게 표현하고 링크의 미리보기를 제공하는 데 사용된다.

Open Graph 메타데이터는 `<meta>` 태그를 사용하여 웹 페이지의 `<head>` 섹션에 추가하면 된다 . `og:title`, `og:type`, `og:description`,`og:image`, `og:url` 등의 다양한 tag를 통해서 메타데이틀 만들어낼 수 있다.

### 1. Open Gragh 있는 경우:

{% linkpreview "https://github.com/ksyu0508/ybigta_chatbot" %}

### 2. Open Graph 없는 경우:

{% linkpreview "https://ksyu0508.github.io/python/2023/06/30/TA-lib.html" %}

## 결론

`Open Graph`가 없는 웹페이지보다 예쁘게 미리보기로 노출될 수 있고, 또한 검색 엔진 최적화(SEO)에도 영향을 미칠 수 있다. 물론 `jekyll`은 기본적으로 `seo-tag`를 제공하고 있기 때문에 크게 영향을 받지는 않을 것이다. 다만, `github`과 같은 사이트들은 `open graph`에 노출되는 이미지를 자동으로 만들어주기에, `jekyll` 블로그에서 자동으로 대표 이미지 태그를 추가하는 내용은 따로 포스팅하도록 하겠다.

