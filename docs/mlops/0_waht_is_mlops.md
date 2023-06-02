---
layout: default
parent: MLOps
title: 0. MLOps란 무엇인가?
nav_order: 1
---

# MLOps란 무엇인가요?
{: .fw-700 }
2023년 6월 2일
{: .d-flex .flex-justify-start .text-grey-dk-000 }

---

## MLOps란 무엇인가요?
{: .text-yellow-300 .fw-700 }

<br>
![ml-lifecycle-mlops-eternal-knot](/assets/images/ml-lifecycle-mlops-eternal-knot.png)

[ MLOps 생애주기 ]
{: .d-flex .flex-justify-around .fw-700 }

<br>
MLOps는 Machine Learning Operations를 의미합니다. 구체적으로는 위 그림과 같이 <strong class="text-yellow-300">데이터 엔지니어링 + 머신 러닝 + 개발 + 운영</strong>의 광범위한 개념입니다.
현업에서 머신 러닝 모델을 실제 서비스 환경인 프로덕션으로 전환하기 위해서는 많은 어려움이 발생하게 됩니다. 

<br>
MLOps는 이러한 어려움을 해소하여 좀 더 빠르고 정확하게 머신러닝 모델을 프로덕션에 배포하는 것을 목표로 합니다. 
나아가 배포된 모델을 유지관리하고 모니터링하여 지속가능한 머신 러닝 서비스를 가능하게 합니다.

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