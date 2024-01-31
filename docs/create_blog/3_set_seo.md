---
layout: post
parent: Github 블로그 만들기
title: 3. 검색 엔진에 블로그 노출 시키기
nav_order: 4
date: 2024-01-31
lastmod: 2024-01-31
sitemap:
  changefreq: daily
  priority: 1.0
---

# 검색 엔진에 블로그 노출 시키기(SEO)
{: .fw-700 .no_toc }
2024년 1월 31일
{: .d-flex .flex-justify-start .text-grey-dk-000 }

---

기본적인 블로그 세팅이 완료되었다면 이제 블로그 포스팅들을 검색 엔진에 노출시켜야 합니다.
구글, 네이버 등 검색 서비스에서는 인터넷에 공개된 웹 페이지들의 구조를 주기적으로 크롤러를 통해 가져갑니다.
이렇게 가져간 정보들을 기반으로 검색 시 사용자들에게 노출시키게 됩니다.
따라서 우리의 포스팅이 검색 엔진에 노출되기 위해서는 크롤러가 접근할 수 있게끔 등록해주어야 합니다.

## 목차
{: .no_toc }

1. TOC
{:toc}

<br>


## Step1. sitemap.xml 생성하기
{: .text-yellow-300 .fw-700 }

<br>
검색 엔진의 크롤러가 내 웹 사이트를 효율적으로 크롤링하기 위해서는 어떤 페이지들을 크롤링 해가야하는지 알려줘야 합니다.
이 때 사용되는 파일이 sitemap.xml 입니다.
sitemap.xml 에는 sitemaps 프로토콜으로 정의 된 내용을 작성할 수 있으며, 
robots.txt 를 통한 자동 감지, 페이지 URL, 페이지 변화의 주기, 우선순위 지정 등을 지원합니다.

{: .note }  
sitemap.xml 파일은 웹 페이지 최상위 경로에 위치시키면 됩니다. :)

sitemap.xml
```xml
---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
        xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd" 
        xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {% for page in site.pages %}
    {% if page.layout == "post" %}
      <url>
        <loc>{{ site.url }}/{{ page.path | replace: '.md', '.html' }}</loc>
        {% if page.lastmod == null %}
          <lastmod>{{ page.date | date: "%Y-%m-%d" }}</lastmod>
        {% else %}
          <lastmod>{{ page.lastmod | date: "%Y-%m-%d" }}</lastmod>
        {% endif %}

        {% if page.sitemap.changefreq == null %}
          <changefreq>daily</changefreq>
        {% else %}
          <changefreq>{{ page.sitemap.changefreq }}</changefreq>
        {% endif %}

        {% if page.sitemap.priority == null %}
            <priority>0.5</priority>
        {% else %}
          <priority>{{ page.sitemap.priority }}</priority>
        {% endif %}

      </url>
    {% endif %}
  {% endfor %}
</urlset>
```

저는 위와 같이 jinja2 템플릿을 활용해서 layout이 post인 페이지들의 URL을 일괄 생성하고,
해당 페이지의 작성일, 수정일, 변경주기, 우선순위 등을 지정 해주었습니다.

해당 내용을 push 및 배포 후 블로그 최상위 경로의 /sitemap.xml 로 접근하면 생성된 내용을 확인할 수 있습니다.

<br>

## Step2. robots.txt 생성하기
{: .text-yellow-300 .fw-700 }

<br>
크롤러가 내 웹 페이지를 순회할 때 접근 제어를 위한 파일입니다.
크롤러에게 허용되는 페이지 경로와 허용하지 않는 페이지 경로를 알려줌으로써 불필요한 크롤링을 막고, 요청에 대한 오버헤드를 줄입니다.

{: .warning }  
robots.txt 는 웹 페이지가 검색 엔진에 노출되는 것을 방지하는 것은 아닙니다. 
웹 페이지가 노출되지 않도록 하려면 `noindex` 로 색인 생성을 차단하거나, 비밀번호로 페이지를 보호해야 합니다.
또한 robots.txt 규칙의 표준은 존재하지만 일부 검색 엔진에서만 지원될 수 있고, 크롤러마다 구문을 다르게 해석하기도 합니다.
따라서 페이지 크롤링에 대한 `권고사항` 을 명시한 파일 정도로 이해하시면 좋습니다.

{: .note }  
robots.txt 파일 또한 웹 페이지 최상위 경로에 위치시키면 됩니다. :)

robots.txt
```text
User-agent: *
Allow: /
Sitemap: https://blog.devinu.org/sitemap.xml
```

저는 모든 크롤러(User-agent)에 대해 모든 경로(/)를 허용해주었습니다.
일부 경로 혹은 복잡한 필터를 구현하고 싶다면 검색 엔진의 robots.txt 가이드를 참고하세요.   
- [Google 크롤러의 robots.txt 작성 가이드](https://developers.google.com/search/docs/crawling-indexing/robots/create-robots-txt?hl=ko#create_rules)
- [Naver 크롤러의 robots.txt 작성 가이드](https://searchadvisor.naver.com/guide/seo-basic-robots)

## Step3. Google 검색 엔진 등록
{: .text-yellow-300 .fw-700 }

<br>
구글에서는 Google Search Console 서비스를 통해 검색 엔진 등록을 지원합니다.
등록 과정은 아래와 같습니다.

1. [Google Search Console](https://search.google.com/search-console) 접속
2. 신규 URL 등록(블로그 최상위 주소를 등록합니다)
3. 소유권 확인하기
   1. 설정 탭 혹은 안내에 따라 소유권 확인 메뉴로 진입
   2. 권장 확인 방법인 HTML 파일 확인
      3. 제공해주는 html 파일 다운로드
      4. 해당 파일을 블로그 최상위에 업로드
5. Sitemap 등록하기
   1. sitemap 탭에서 /sitemap.xml 경로를 등록 해줍니다.

해당 과정이 완료되고 시간이 지나면 구글 크롤러가 내 웹 페이지를 크롤링하기 시작합니다.   

{: note }  
크롤링 시작 및 분석 결과 표출까지 1~2일의 시간이 걸릴 수 있으니 차분히 기다려봅시다.

<br>


## Step4. Naver 검색 엔진 등록(선택)
{: .text-yellow-300 .fw-700 }

<br>
기술 블로그는 일반적으로 google 검색을 통해 유입됩니다. 따라서 네이버 검색 엔진에는 굳이 등록할 필요가 없지만 선택적으로 등록할 수 있습니다.
네이버에서는 Naver Search Advisor 서비스를 통해 웹 페이지 검색을 지원합니다.

- [Naver Search Advisor](https://searchadvisor.naver.com/)

해당 페이지의 웹 마스터 도구를 통해 내 사이트를 등록하고, 가이드에 알맞게 등록 과정을 진행합니다.  
(소유권 확인, 사이트맵 제출)

이제 시간이 지나면 내 블로그가 검색 엔진에 노출되게 됩니다.