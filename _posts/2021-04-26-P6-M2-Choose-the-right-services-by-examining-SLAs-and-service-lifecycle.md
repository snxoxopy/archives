---
title:  "[Cloud] P6_M2_Choose the right Azure services by examining SLAs and service lifecycle"
excerpt: Part6/Module2/SLA 및 서비스 수명 주기를 검토하여 적합한 Azure 서비스 선택
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

## Module 2 - **Learning objectives**

After completing this module, you'll be able to:

- Describe what a service-level agreement (SLA) is and why SLAs are important.
- Identify factors, such as the service tier you choose, that can affect an SLA.
- Combine SLAs to compute a composite SLA.
- Describe the service lifecycle in Azure, including how to access new capabilities that are coming to Azure.

## 1. 서비스 준수 약정 및 수명 주기

### 1.1 Azure 서비스 수준 약정(SLA)

- SLA: Service Level Agreements
- SLA에는 MS에서 제시하는 작동시간 및 연결 약정 관련 설명이 나와있다.
- SLA는 개별 제품과 서비스를 기준으로한다.
- 제공되는 서비스 관련 세부 계약과 SLA 예외 사항도 제시
- 무료 및 미리 보기 기능/서비스 에서는 SLA가 제공되지 않는다.

### 1.2 Azure 제품 및 서비스에 대한 SLA

- 성능 목표는 가동시간(uptime) 및 연결보장(connectivity)로 표현된다.
- 성능 목표는 99% ~ 99.999%
- 서비스가 보장 내용을 충족하지 못하는 경우 월별 서비스 요금의 일정 비율을 Credit으로 받을 수 있다.

### 1.3 SLA에 영향을 주는 작업

- SLA는 사업 목표에 따라 디자인을 결정하면 SLA 목표도 함께 결정 가능
- SLA 낮추기
    - 서비스를 추가할 수록 SLA가 낮아짐
    - 무료 서비스나 SLA가 없는 서비스 선택
- SLA 높이기
    - 가용성 영역
    - 중복 시스템

### 1.4 Azure 제품 및 기능 수명 주기

- Azure 미리 보기 프로그램
    - 베타 및 기타 시험판 기능, 제품, 서비스, SW 및 지역을 테스트하여 피드백 제공 가능
    - 공개 미리보기: 모든 Azure 고객은 새 기능을 평가 가능
    - GA(일반 공급): 공개 미리 보기가 완료되면 모든 고객이 기능을 사용 가능. 지역별로 기능 사용 가능 여부가 다르다.
- 서비스 및 기능 업데이트 모니터링
    - Azure 업데이트는 Azure 제품, 서비스, 기능, 제품 로드맵과 가용성 관련 정보를 제공
    - 모든 Azure 업데이트 및 해당 상태에 대한 세부 정보를 확인
    - 업데이트를 찾아보고 검색
    - 구독을 신청하여 RSS로 Azure 업데이트 알림을 받기

### 1.5 Knowledge Check

Tailwind Traders의 Special Orders 애플리케이션에는 Azure Load Balancer와 Azure SQL Database라는 두 대의 가상 머신이 포함되어 있습니다.

![https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/choose-azure-services-sla-lifecycle/media/4-special-orders-architecture.svg](https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/choose-azure-services-sla-lifecycle/media/4-special-orders-architecture.svg)

각 서비스에 대한 SLA(서비스 수준 계약)는 다음과 같습니다. (Service: SLA)

- Azure Virtual Machines: 99.%
- Azure SQL Database: 99.99%
- Azure Load Balancer: 99.99%

서비스 집합의 복합 SLA를 계산하려면 개별 서비스의 SLA를 곱합니다. 기존 복합 SLA는 다음과 같습니다.

99.9%×99.9%×99.99%×99.99%=99.78%99.9%×99.9%×99.99%×99.99%=99.78%

팀은 근처 공급업체와 각 소매 매장 간의 경로를 계산할 수 있도록 매핑 기능을 추가하려고 합니다. 이를 위해 Azure Maps를 사용합니다.

또한 팀은 수요에 대처하기 위해 더 많은 처리 능력이 필요합니다. 이를 위해 세 번째 가상 머신을 풀에 추가합니다.

다음은 제안된 계획을 보여 주는 다이어그램입니다.

![https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/choose-azure-services-sla-lifecycle/media/6-special-orders-architecture-maps.svg](https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/choose-azure-services-sla-lifecycle/media/6-special-orders-architecture-maps.svg)

Tailwind Traders에서는 Special Orders 앱에서 고객이 사용자 지정을 시각화할 수 있도록 증강 현실 서비스 사용을 고려하고 있습니다. 해당 Azure 서비스는 현재 공개 미리 보기 단계에 있습니다.

Q. 보장된 작동 시간 측면에서 Azure Maps의 SLA는 무엇인가요?

1. 99%
2. 99.9%
3. 99.99%

Q. 새 복합 SLA는 무엇인가요? 새 SLA에는 세 번째 가상 머신과 Azure Maps가 포함됩니다.

1. 99.58%
2. 99.78%
3. 99.99%

Q. 세 번째 가상 머신을 추가하면 복합 SLA가 줄어듭니다. Tailwind Traders에서 이 감소를 어떻게 상쇄할 수 있나요?

1. 각 가상 머신의 크기를 늘립니다.
2. 동일한 Azure 지역의 다른 가용성 영역에 동일한 가상 머신의 추가 인스턴스를 배포한다.
3. 아무 작업도 하지 않는다. Azure Load Balancer를 사용하면 가상 머신의 SLA가 향상

Q. 이 회사에서 아키텍처에 AR(증강 현실) 미리 보기 서비스를 추가하는 데 사용할 수 있는 방법은 무엇인가요?

1. Special Orders 앱은 이미 프로덕션 단계에 있습니다. 이 회사는 서비스가 GA에 도달할때까지 AR 서비스를 고려하지 않아야 한다.
2. Special Orders 앱은 주로 소매 직원이 사용. 잠재적 가동 중지 시간 또는 오류가 중요한 요소가 아니므로 이제 AR 서비스를 통합 가능
3. 개발 팀은 AR 서비스를 포함하는 앱의 프로토타입 버전을 만들어 선정된 소매 직원에게 테스트하도록 할 수 있다.

> SHOUT OUT TO  
> [[MS Learn] SLA 및 서비스 수명 주기를 검토하여 적합한 Azure 서비스 선택](https://docs.microsoft.com/ko-kr/learn/modules/choose-azure-services-sla-lifecycle/)
> [Microsoft Azure Virtual Training Day: Fundamentals](http://www.microsoft.com/ko-kr/events/training-days)

### 1.6 Answer

[2]: Microsoft는 Azure Maps를 99.9% 이상의 시간에 이용할 수 있다는 것을 보장합니다.

[1]: 서비스 집합의 복합 SLA를 계산하려면 개별 서비스의 SLA를 곱합니다.

[2]: 하나의 가용성 영역에 영향을 주는 경우 다른 가용성 영역에 있는 가상 머신 인스턴스는 영향을 받지 않습니다.

[3]: AR 서비스가 GA(일반 공급)에 도달한 후 팀은 프로덕션으로 롤아웃할 수 있습니다.