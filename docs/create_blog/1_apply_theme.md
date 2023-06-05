---
layout: post
parent: Github 블로그 만들기
title: 1. 블로그 테마 적용하기
nav_order: 2
date: 2023-06-03
sitemap:
  changefreq: daily
  priority: 1.0
---

# 블로그 테마 적용하기
{: .fw-700 .no_toc }
2023년 6월 3일
{: .d-flex .flex-justify-start .text-grey-dk-000 }

---

## 목차
{: .no_toc }

1. TOC
{:toc}

## Step1. Jykell 블로그 테마 탐색
{: .text-yellow-300 .fw-700 }

<br>
Github Pages를 활용해 블로그를 구성하기 위해서는 정적 페이지를 직접 구현할 수 있지만 이는 모든 페이지를 직접 구현해야 하기 때문에 비효율적입니다. 정적 페이지 생성기를 활용하면 원하는 형태의 블로그를 빠르게 생성할 수 있습니다. Github Pages에서는 대표적으로 Jekyll 정적 페이지 생성기를 지원합니다.

<br>
아래 사이트에서 마음에 드는 Jekyll 테마를 찾아보세요. 여기서는 `Just-the-docs`를 적용해보겠습니다.

- Jekyll 테마 페이지 : [Jekyll Themes](https://jekyll-themes.com/free)
- Just-the-docs Github 페이지 : [Just the Docs](https://github.com/just-the-docs/just-the-docs)

## Step2. 테마 소스코드 내 저장소로 Fork 하기
{: .text-yellow-300 .fw-700 }

<br>
마음에 드는 테마를 찾았다면 해당 테마를 내 저장소로 Fork하여 활용할 수 있습니다. 테마의 소스코드 저장소에서 우측 상단의 [Fork] 버튼을 클릭하여 내 저장소로 Fork 합니다.

![apply-theme-0](/assets/images/apply_theme_0.png)
{: .d-flex .flex-justify-around }

[ 테마 Fork 하기 ]
{: .d-flex .flex-justify-around .fw-700 }

## Step3. 테마 적용하기
{: .text-yellow-300 .fw-700 }

<br>
`_config.yml` 파일 내의 `remote_theme` 설정을 통해 Fork한 내 원격 저장소의 테마를 바로 적용할 수 있습니다.

```yaml
remote_theme: develinu/just-the-docs

title: Devinu's Blog
description: Devinu's Blog
baseurl: "/"
url: "https://blog.devinu.org"
```

![apply-theme-1](/assets/images/apply_theme_1.png)
{: .d-flex .flex-justify-around }

[ 적용된 테마 화면 ]
{: .d-flex .flex-justify-around .fw-700 }

## Step4. 테마 설정하기
{: .text-yellow-300 .fw-700 }

<br>
`_config.yml` 내에서 다양한 옵션들을 통해 블로그의 레이아웃과 색상, 기능 등을 조정할 수 있습니다. 설정에 대한 자세한 내용은 아래 `Just-the-docs`의 공식 문서를 참고하세요.

- [Just the Docs 공식 문서](https://just-the-docs.github.io/just-the-docs/)

저는 문서를 참고하여 아래와 같이 세팅해주었습니다.

```yaml
remote_theme: develinu/just-the-docs

title: Devinu's Blog
description: Devinu's Blog
baseurl: "/"
url: "https://blog.devinu.org"

search_enabled: false

mermaid:
  version: "9.1.3"

aux_links:
  "GitHub":
    - "//github.com/develinu"

aux_links_new_tab: true

color_scheme: dark

callouts:
  note:
    title: 정보
    color: green
  warning:
    title: 주의
    color: yellow
  error:
    title: 경고
    color: red
```
[ _config.yml ]
{: .d-flex .flex-justify-around .fw-700 }

<br>

![apply-theme-2](/assets/images/apply_theme_2.png)
{: .d-flex .flex-justify-around }

[ 최종 적용된 테마 화면 ]
{: .d-flex .flex-justify-around .fw-700 }