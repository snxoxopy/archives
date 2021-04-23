---
title:  "[Cloud] P1_M2_Discuss Azure fundamental concepts"
excerpt: Part1/Module2/Azure 기본 개념 설명
toc: True
toc_sticky: True
toc_label: "Contents"
sidebar:
  nav: "docs"
categories:
  - cloud
tags:
  - az-900
---

# Module 2 학습목표

- Cloud Computing 이점 및 주요 용어 이해
- IaaS, Pass, and SaaS Cloud Service 이해
- Public, Private 및 Hybrid Cloud Computing 이해

## 1. Cloud Computing 개념
### 1.1 Cloud Computing 이란?
> Internet 상에서 Computing Resource에 접속할 수 있도록 제공하는 것

### 1.2 Cloud Computing 이점
- Fault tolerance
  - 장애는 언제나 발생 가능
  - 장애 발생시 대응예
    - 복사본으로 대체
    - Back-up 복원

- High availability
   - 한 Data Centre 내에 장비 문제 발생 시, 대응 가능한 것
   - 장애발생 시간을 최소한으로 줄이는 것
   - Fault  tolerance의 한 부분

- Elasticity
  - 즉각적인 확장/축소 능력
  - 사용하지 않을 때 축소 가능

- Scalability
  - 즉각적인 Scale Up/Out 가능
  - 필요시 확장 가능
  
- Agility
  - 확장 필요시 즉각적으로 Server를 배포하고, Service를 지속적으로 이어갈 수 있도록 하는 능력
  - Scalability 관련한 이점
  
- Global reach
  - 고객이 Workload를 높여 사용 하고자할 때, 물리적으로 Resource를 가까이 위치하여 End User로 하여금 Low latency로 Service 이용 가능하게 하는 것

- Customer latency
  - 고객사의 최종 사용자에게 신속한 Service를 사용할 수 있도록 함
    - Data Centre를 현지에 위치하게 하여 최종 사용자가 빠른 속도로 Service를 이용할 수 있게 함
  - Global reach 관련한 이점
 

- Predictive cost
  - Public Cloud Service는 사용량을 측정할 수 있도록 설계됨
  - 비용 예측이 빠름
  
### 1.3 Economics of scale
- Cloud 제공업체는 규모 경제의 이점을 활용하여 그 혜택을 고객에게 배분하는 것이 가능하다.

> 규모 경제: 작은 규모로 운용하는 것에 비해 더 큰 규모로 운영할 때 저럼하고 효율적으로 작업을 수행할 수 있는 능력을 말한다.

### 1.4 CapEx vs. OpEx
- CapEx: Capital Expenditure
  - 물리적 Infra에 대한 지출을 선불로 지불
  - 시간이 지남에 따라 세금 계산서에 비용을 공제
  - 높은 초기비용, 투자 가치는 시간에 따라 감소
  
- OpEx: Operational Expenditure
  - 필요에 따라 Service 또는 제품에 지출되고 즉시 청구
  - 같은 해에 세금 계산서에 비용을 공제
  - 선 결제 비용이 없고, 종량제 사용
  
 - Ex) Public Cloud 사용시 운영 비용만 발생한다. 반면, 직접 Data Centre를 운영시, 자본 지출 발생한다.

### 1.5 Exercises
Q. 다음 중 클라우스 서비스의 이점을 설명한 항목은?

1. 규모의 경제
2. 고정된 워크로드
3. 예측할 수 없는 비용

Q. 다음 중 클라우드 서비스를 사용하면 얻게 되는 이점이 아닌 것은 무엇인가요?

1. 확장성
2. 지역 격리
3. 재해 복구
4. 고가용성

Q. 다음 중 장기간 가동 중지 기간 없이 서비스를 사용할 수 있도록 하는 특성은 무엇입니까?

1. 민첩성
2. 내결함성
3. 고가용성
4. 성능

Q. 다음 중 미리 지불한 후 시간이 지남에 따라 공제되는 비용을 나타내는 용어는 무엇입니까?

1. 자본지출
2. 운영비용
3. 공급과 수요

Q. 다음 중 참인 것은 무엇인가요?

1. OpEx에서는 컴퓨팅 리소스의 구매와 유지 관리를 책임집니다.
2. OpEx에서는 사용하는 컴퓨팅 리소스에 대해서만 책임집니다.
3. CapEx에서는 사용하는 컴퓨팅 리소스에 대해서만 책임집니다.


---
> **SHOUT OUT TO**
> 
>[[MS-Learn] 클라우드 컴퓨팅의 이점 설명](https://docs.microsoft.com/ko-kr/learn/modules/fundamental-azure-concepts/benefits-of-cloud-computing)  
>[[오구사십오] Day1 Module01 - 클라우드 개념](https://ogu45.com/zbxe/school/82708)

### 1.6 Answer

[1]

[2] 
- **해설**
  - 재해 복구: 클라우드 컴퓨팅은 재해 복구를 지원하는 다양한 기술을 제공
  - 지역 격리: 단일 지역에서 리소스를 만들도록 선택할 수 있지만, 클라우드 컴퓨팅의 주요 이점 중 하나는 지리적 분산

[3]

[1]

[2]
- **해설**
  - CapEx(자본 비용)에서는 사용하는 컴퓨팅 리소스뿐만 아니라 컴퓨팅 리소스의 구매 및 유지 관리에 대해서도 책임집니다.

---

## 2. Cloud Service Models
> Cloud Service Model 이란?
> 
>  공급자와 Tenant가 담당하는 서로 다른 수준의 공유 책임을 정의한 Model
> ![](https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/fundamental-azure-concepts/media/iaas-paas-saas-expanded.png#lightbox)

### 2.1 IaaS: Infrastructure-as-a-Service
![](https://ogu45.com/zbxe/files/attach/images/96/708/082/5cb7d94c2ad6ba5718fb8e94474a7ba7.jpg)

- 가장 유연한 Cloud Service
- Cloud 공급자로부터 아래 항목을 **_"대여"_** 하여 종량제 IT Infra를 구축
  - Servers, Virtual Machine, Storage, OS, Networking firewalls/Security, Datacentre physical plant/building
- 고객이 Application을 위한 HW를 구성하고 관리
- Application을 실행하는 OS를 구성하고 관리할 수 있는 제어력 보유

|Items|공급자가 관리|사용자가 관리|
|---|:---:|---:|
|Data & Access|-|O|
|Applications|-|O|
|Runtime|-|O|
|Operating System|-|O|
|Virtual Machine|-|O|
|Compute|O|-|
|Networking|O|-|
|Storage|O|-|

### 2.2 PaaS: Platform-as-a-Service 
![](https://ogu45.com/zbxe/files/attach/images/96/708/082/184b4b51534770854018abc8f7835cf7.jpg)
- 기본 Infra 관리에 신경쓰지 않고 SW Application을 Build, Test 및 Release 할 수 있는 환경을 제공
- Application 개발에 집중
- Platform 관리는 Cloud 공급자가 처리

|Items|공급자가 관리|사용자가 관리|
|---|:---:|---:|
|Data & Access|-|O|
|Applications|-|O|
|Runtime|O|-|
|Operating System|O|-|
|Virtual Machine|O|-|
|Compute|O|-|
|Networking|O|-|
|Storage|O|-|


### 2.3 SaaS: Software-as-a-Service
![](https://ogu45.com/zbxe/files/attach/images/96/708/082/14611f720a4b57f8587938aa14184a7c.jpg)

- 사용자는 Internet을 통해 MS Office 365, e-mail, Calendar와 같은 Cloud 기반 App에 연결하고 사용
- 사용자는 구독 Model을 통해 사용하는 SW에 대해 비용을 지불
- 종량제 가격 Model

|Items|공급자가 관리|사용자가 관리|
|---|:---:|---:|
|Data & Access|-|O|
|Applications|O|-|
|Runtime|O|-|
|Operating System|O|-|
|Virtual Machine|O|-|
|Compute|O|-|
|Networking|O|-|
|Storage|O|-|

### 2.4 Shared responsibility model
![](https://images.velog.io/images/snoo_py/post/69fd75fb-f28c-42d9-a654-7834614fa2e4/image.png)


### 2.5 Exercises

Q. Microsoft Office 365는 무엇의 예입니까?

1. 서비스형 인프라 (IaaS)
2. 서비스형 플랫폼 (PaaS)
3. 서비스형 소프트웨어 (SaaS)

Q. 다음 중 PaaS(서비스형 플랫폼)를 설명한 항목은 무엇입니까

1. 사용자는 운영체제, 미들웨어 및 애플리케이션 드 자체 소프트웨어를 구매, 설치, 구성 및 관리할 책임이 있다.
2. 사용자는 기본 인프라 관리에 대해 걱정할 필요 없이 신속하게 애플리케이션을 만들고 배포할 수 있다.
3. 사용자는 연간 또는 월간 구독료를 지불한다.

Q. 다음 중 사용자의 관리가 가장 많이 필요한 클라우드 서비스는 무엇입니까?

1. 서비스형 인프라
2. 서비스형 플랫폼
3. 서비스형 소프트웨어

---
> **SHOUT OUT TO**
> 
>[[MS-Learn] 클라우드 서비스의 여러 범주 설명](https://docs.microsoft.com/ko-kr/learn/modules/fundamental-azure-concepts/categories-of-cloud-services)  
>[[오구사십오] Day1 Module01 - 클라우드 개념](https://ogu45.com/zbxe/school/82708)

### 2.6 Answer

[3]

[2]

[1]

---

## 3. Deployment model: Cloud Computing 유형

### 3.1 Public Cloud

- Cloud Service 또는 Hosting 공급자가 소유
- 여러 조직과 사용자에게 Resource와 Service를 제공
- 일반적으로 Internet을 연결하여 접근 또는 보안 Network를 연결하여 접근
- 한 고객만을 위해 Service가 제공되지 않고 공용 공간으로 관리
- IaaS, PaaS, SaaS

### 3.2 Private Cloud

- 하나의 기업 또는 조직의 선택된 사용자만 독점적으로 사용하는 Computing Resource로 구성
- 조직의 On-premises Datacentre에 있을 수 있거나, 타사 Service 공급자가 Host 할 수 있음
- Cloud Resource를 사용하는 조직에서 소유하고 운영
- 조직에게 본인들이 제공하는 Service를 운영할 책임이 있음

### 3.3 Hybrid Cloud

- Cloud를 결합하는 Computing 환경
- Public과 Private Cloud 사이의 Data 및 Application을 공유할 수 있도록 함
- Cloud 또는 On-premises에서 Application을 실행할 수 있다.

### 3.4 Deploy Model 비교

|Public Cloud|Private Cloud|Hybrid Cloud|
|:-----------|:------------|:-----------|
|CapEx X: 확장하기 위해 Server 구입 할 필요 없음|제어력: 조직은 Resource를 완벽하게 제어 가능|유동성: 업체는 Private 또는 Public Cloud에서 실행할지의 여부를 결정|
|Agility: Application 빠른 접근 가능, 필요시 Provisioning 해제 가능|보안: 조직은 보안을 완벽하게 제어 가능|준수성: 조직은 필요에 따라 엄격한 보안, 규정 준수 또는 법적 요구사항을 준수할 수 있는 기능을 유지|
|소비기반 Model: 조직은 OpEx 모델로 사용하고 운영하는 것에 대해서만 비용 지불|-|-|


### 3.5 Exercises

Q. 어떤 클라우드 컴퓨팅 유형이 가장 높은 수준의 소유권과 제어를 제공합니까?

1. 하이브리드
2. 프라이빗
3. 공용

Q. 어떤 클라우드 컴퓨팅 유형이 가장 큰 유연성을 제공합니까?

1. 공용
2. 프라이빗
3. 하이브리드

Q. 다음 중 공용 클라우드를 설명한 항목은 무엇입니까?

1. 해당 클라우드의 리소스를 사용하는 조직에서 소유하고 운영한다.
2. 클라우드 또는 온-프레미스에서 애플리케이션을 실행할 수 있다.
3. 보안 네트워크 연결을 통해 연결하는 여러 조직 및 사용자에게 리소스와 서비스를 제공한다.

Q. 전문 메인프레임 하드웨어가 필요한 레거시 애플리케이션과 최신의 공유 애플리케이션이 있는 경우, 어떤 클라우드 배포 모델이 적합합니까?
1. 공용 클라우드
2. 프라이빗 클라우드
3. 하이브리드 클라우드

---
> **SHOUT OUT TO**
> 
>[[MS-Learn] 여러 클라우드 컴퓨팅 유형 설명](https://docs.microsoft.com/ko-kr/learn/modules/fundamental-azure-concepts/types-of-cloud-computing)  
>[[오구사십오] Day1 Module01 - 클라우드 개념](https://ogu45.com/zbxe/school/82708)

### 3.6 Answer

[2]

[3]

[3]

[3]

---
