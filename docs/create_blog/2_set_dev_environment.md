---
layout: post
parent: Github 블로그 만들기
title: 2. 로컬 개발 환경 만들기(for Windows)
nav_order: 3
date: 2023-06-09
sitemap:
  changefreq: daily
  priority: 1.0
---

# 로컬 개발 환경 만들기(for Windows)
{: .fw-700 .no_toc }
2023년 6월 9일
{: .d-flex .flex-justify-start .text-grey-dk-000 }

---

이전 포스팅에서 Github Pages와 Jekyll을 활용하여 블로그를 만드는 방법을 알아보았습니다.

하지만 블로그 웹을 코드 기반으로 직접 관리하는 형태이기 때문에 포스팅이나 테마 변경 등의 코드 변경을 적용하기 전에 로컬에서 테스트 해본 뒤에 변경사항을 게시하는 것이 좋습니다. 

또 포스팅 도중에 글의 레이아웃이나 전체적인 느낌을 보고 싶을 때 중간 결과를 업로드 하게 되면 유저들에게 정제되지 않은 글이 노출된다는 단점이 있습니다.

그리고 매 번 CI/CD 파이프라인이 완료되고 블로그 페이지가 업데이트 되기까지 기다려야 되는 번거로움이 발생합니다.

이번에는 로컬 개발 환경을 만들어서 이러한 불편함을 해결해 보겠습니다.

{: .note }  
본 문서는 Windows 환경을 기준으로 작성되었습니다.

## 목차
{: .no_toc }

1. TOC
{:toc}

<br>

## Step1. Ruby 설치하기
{: .text-yellow-300 .fw-700 }

<br>
Jekyll은 루비 프로그래밍 언어로 개발되었습니다. 따라서 Jekyll 기반 페이지를 생성하기 위해서는 Ruby가 설치되어야 합니다. 아래 링크를 통해 Windows용 최신 버전 루비를 설치하시면 됩니다.

{: .note }  
저는 Ruby 3.2.2-1-x64 버전을 사용했습니다.

- [Windows용 루비 다운로드 페이지](https://rubyinstaller.org/downloads/)

### 설치 순서
{: .no_toc }
1. 설치 모드 선택 : Install for me only
2. 라이선스 동의
3. 설치 경로 지정 및 환경관련 체크박스 모두 체크
  - ![set-dev-environment-0](/assets/images/set_dev_environment_0.png)
4. 설치 항목 모두 체크
  - ![set-dev-environment-1](/assets/images/set_dev_environment_1.png)
5. 설치가 완료되면 MSYS2 개발 툴체인 추가 설치를 체크하고 완료합니다.
  - ![set-dev-environment-2](/assets/images/set_dev_environment_2.png)
6. 다음 화면에서 입력 없이 `ENTER`를 눌러 설치를 계속 진행해줍니다.
  - ![set-dev-environment-3](/assets/images/set_dev_environment_3.png)
7. 설치가 완료되면 다시 한 번 `ENTER`를 눌러 설치를 완료합니다.

<br>

## Step2. Jeykll 설치하기
{: .text-yellow-300 .fw-700 }

<br>
Ruby를 설치하셨다면 다음으로 Jeykll을 설치해야 합니다. 그리고 관련 의존성을 관리하기 위한 Bundler도 설치합니다.

아래 명령을 통해 Jeykll과 Bundler를 설치해주세요.

```bash
gem install jeykll bundler
```

![set-dev-environment-4](/assets/images/set_dev_environment_4.png)
{: .d-flex .flex-justify-around }

[ Jeykll, Bundler 설치 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>

## Step3. GemFile 작성하기
{: .text-yellow-300 .fw-700 }

<br>
`GemFile` 파일을 통해 Jeykll 실행에 필요한 의존성을 정의해줍니다.

```bash
source "https://rubygems.org"

# # do NOT include the jekyll gem !
gem "github-pages", group: :jekyll_plugins
gem "kramdown-parser-gfm"
gem "webrick", "~> 1.8"
```

아래 명령을 통해 Bundler가 의존성을 설치하도록 합니다.

```bash
bundle install
```

<br>

## Step4. 로컬 환경용 설정 파일 만들기
{: .text-yellow-300 .fw-700 }

<br>
이전 포스팅에서 `_config.yml` 에서 블로그의 테마와 기능 등을 정의해주었습니다. 이 설정 파일에서 블로그의 주소 또한 지정해주게 되는데 로컬 환경에서 실행하기 위해서는 이 주소를 로컬 호스트의 url로 변경되어야 합니다.

로컬 환경용 `_config_dev.yml` 파일을 생성하고, 로컬 호스트 url을 지정해줍니다.

```yaml
url: http://localhost:4000
```
[ _config_dev.yml ]
{: .d-flex .flex-justify-around .fw-700 }

<br>

## Step5. 로컬 환경 서버 실행하기
{: .text-yellow-300 .fw-700 }

<br>
이제 아래 명령을 통해 로컬 환경에서 서버를 실행할 수 있습니다.

```bash
bundle exec jekyll serve --config "_config.yml,_config_dev.yml"
```

![set-dev-environment-5](/assets/images/set_dev_environment_5.png)
{: .d-flex .flex-justify-around }

[ 로컬 환경 Jeykll 서버 실행 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>

![set-dev-environment-6](/assets/images/set_dev_environment_6.png)
{: .d-flex .flex-justify-around }

[ 로컬 서버 수행 화면 ]
{: .d-flex .flex-justify-around .fw-700 }