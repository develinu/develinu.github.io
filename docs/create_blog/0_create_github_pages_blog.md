---
layout: default
parent: Github 블로그 만들기(for Windows)
title: 0. 블로그용 Github 저장소 만들기
nav_order: 1
---

# 블로그용 Github 저장소 만들기
{: .fw-700 }
2023년 6월 3일
{: .d-flex .flex-justify-start .text-grey-dk-000 }

---

## Step1. 블로그용 Github 저장소 만들기
{: .text-yellow-300 .fw-700 }

<br>
참고자료 : [Github Pages 공식 문서](https://docs.github.com/ko/pages/quickstart)

<br>
① Github의 우측 상단 [+] 버튼을 눌러 새 저장소를 생성합니다.

<br>
![create-blog-0](/assets/images/create_blog_0.png)

[ 새 저장소 생성 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
② 저장소 이름을 `username.github.io` 형식으로 지정하여 저장소를 생성합니다.

<br>
![create-blog-1](/assets/images/create_blog_1.png)

[ 저장소 이름 지정 및 생성 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
③ 생성된 저장소의 [Settings] 탭에서 좌측의 [Pages] 탭으로 진입합니다.   
배포 소스를 브랜치에서 가져오도록 설정하고, 배포 대상 브랜치를 main으로 선택합니다.   
별도로 구매한 도메인이 있다면 이 탭에서 사용자 도메인을 연결할 수도 있습니다.

<br>
![create-blog-2](/assets/images/create_blog_2.png)

[ Github Pages 설정 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
④ `_config.yml` 파일의 설정을 통해 블로그의 이름과 테마 등을 지정할 수 있습니다.   
```yaml
title: Devinu's Blog
description: Devinu's Blog
baseurl: "/"
url: "https://blog.devinu.org"
```

<br>
![create-blog-3](/assets/images/create_blog_3.png)

[ _config.yml 파일 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
MLOps는 Machine Learning Operations를 의미합니다. 구체적으로는 위 그림과 같이 <strong class="text-yellow-300">데이터 엔지니어링 + 머신 러닝 + 개발 + 운영</strong>의 광범위한 개념입니다.
현업에서 머신 러닝 모델을 실제 서비스 환경인 프로덕션으로 전환하기 위해서는 많은 어려움이 발생하게 됩니다.

---

## 왜 필요한가요?
{: .text-yellow-300 .fw-700 }

<br>
최근 AI가 급부상하면서 많은 기업에서 머신 러닝 기술을 도입하기 시작했습니다. 
사실 이미 많은 기업에서 활용하고 있었지만 점점 많은 수의 머신러닝 프로젝트를 진행함에 따라 모델을 배포하고 관리하는 것이 큰 어려움으로 자리잡게 되었습니다. 
또한 머신 러닝 프로젝트의 특성상 <strong class="text-yellow-300">모델의 성능과 데이터 품질에 대한 지속적인 관찰 및 대응 프로세스</strong>가 필요하게 되었습니다.
이는 전통적인 애플리케이션 모니터링과는 조금 다른 특징과 프로세스를 필요로 하며, 이를 빠르고 일관성 있게 수행하기 위해서는 MLOps가 필요합니다.

<br>
MLOps에 대해서 구체적으로 들여다보기 전에 먼저 머신러닝 프로젝트가 어떤 방식으로 진행되는지 살펴볼 필요가 있습니다.
<strong>이후 글에서는 머신러닝 프로젝트가 실제로 어떻게 진행되며 어떤 부분에서 어려움이 발생하는지 차근차근 정리해 볼 예정입니다.</strong>