---
layout: post
parent: Github 블로그 만들기
title: 0. 블로그용 Github 저장소 만들기
changefreq: weekly
nav_order: 1
date: 2023-06-03
sitemap:
  changefreq: daily
  priority: 1.0
---

# 블로그용 Github 저장소 만들기
{: .fw-700 }
2023년 6월 3일
{: .d-flex .flex-justify-start .text-grey-dk-000 }

---

{: .note }  
참고자료 : [Github Pages 공식 문서](https://docs.github.com/ko/pages/quickstart)

## Step1. 블로그용 Github 저장소 만들기
{: .text-yellow-300 .fw-700 }

<br>
① Github의 우측 상단 [+] 버튼을 눌러 새 저장소를 생성합니다.

![create-blog-0](/assets/images/create_blog_0.png)
{: .d-flex .flex-justify-around }

[ 새 저장소 생성 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
② 저장소 이름을 `username.github.io` 형식으로 지정하여 저장소를 생성합니다.

![create-blog-1](/assets/images/create_blog_1.png)
{: .d-flex .flex-justify-around }

[ 저장소 이름 지정 및 생성 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
③ 생성된 저장소의 [Settings] 탭에서 좌측의 [Pages] 탭으로 진입합니다.   
배포 소스를 브랜치에서 가져오도록 설정하고, 배포 대상 브랜치를 main으로 선택합니다.   
별도로 구매한 도메인이 있다면 이 탭에서 사용자 도메인을 연결할 수도 있습니다.

![create-blog-2](/assets/images/create_blog_2.png)
{: .d-flex .flex-justify-around }

[ Github Pages 설정 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>

## Step2. _config.yml 파일 만들기
{: .text-yellow-300 .fw-700 }

<br>
`_config.yml` 파일의 설정을 통해 블로그의 이름과 테마 등을 지정할 수 있습니다.   
url에는 별도의 도메인이 없다면 `https://<username>.github.io`로 설정하시면 됩니다.

```yaml
title: Devinu's Blog
description: Devinu's Blog
baseurl: "/"
url: "https://blog.devinu.org"
```

[ _config.yml ]
{: .d-flex .flex-justify-around .fw-700 }

<br>

## Step3. index.md 파일 만들기
{: .text-yellow-300 .fw-700 }

<br>
`index.md` 파일을 생성하고 Markdown 텍스트를 채워넣은 뒤 해당 저장소를 업데이트 해주세요.   
main 브랜치의 변경사항이 push되면 자동으로 페이지가 빌드됩니다.   
빌드가 완료되면 `https://develinu.github.io`와 같이 해당 저장소 주소로 접속하여 확인할 수 있습니다.   

```markdown
# Devinu
| Machine Learning Engineer

MLOps에 관심이 많은 엔지니어입니다.   
현재는 MLOps와 AI 관련 강사로 활동하고 있습니다.
```

[ index.md ]
{: .d-flex .flex-justify-around .fw-700 }

<br>

![create-blog-4](/assets/images/create_blog_4.png)
{: .d-flex .flex-justify-around }

[ Github Pages 메인(index.md) 화면 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
저장소 업데이트 후 자동 빌드에 대한 현황은 저장소 내 [Actions] 탭에서 확인할 수 있습니다.

![create-blog-5](/assets/images/create_blog_5.png)
{: .d-flex .flex-justify-around }

[ Actions 화면 ]
{: .d-flex .flex-justify-around .fw-700 }