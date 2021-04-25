---
title:  "[Cloud] P6_M1_Plan and manage you Azure costs"
excerpt: Part6/Module1/Azure 비용 계획 및 병합하기
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

## Module 1 - Learning objectives

After completing this module, you'll be able to:

- Use the Total Cost of Ownership Calculator to compare your current datacenter costs to running the same workloads on Azure.
- Describe the different ways you can purchase Azure products and services.
- Use the Pricing calculator to estimate the monthly cost of running your cloud workloads.
- Define some of the major factors that affect total cost and apply recommended practices to minimize cost.

## 1. 계획 및 비용 관리

### 1.1 비용에 영향을 주는 요인

1. 리소스 종류
2. 서비스
3. 위치
4. 대역폭
    - 일부 인바운드 데이터 전송은 무료
    - 아웃바운드 데이터 전송 가격은 영역을 기준으로 책정
5. 예약 인스턴스
6. Azure 하이브리드 사용 혜택

### 1.2 비용 관리

- 보고: 청구 보고서
- 데이터 보강
- 예산: 지출예산 설정
- 알림: 비용 한도 초과시
- 권장 사항: 비용 관련 권장사항 제공

### 1.3 가격 계산기

- Azure 제품의 비용을 예측할 수 있는 도구
- 기봉 구성 옵션
    - 지역
    - 계층
    - 청구옵션
    - 지원 옵션
    - 프로그램/혜택
    - Azure 개발/테스트 가격

### 1.4 Total const on calculator: 총 소유 비용 계산기

- Azure로 마이그레이션하여 실현할 수 있는 비용 절감 예측 도구
- 보고서에 On-premises 인프라 비용과 Azure 제품 및 서비스를 클라우드에서 인프라를 호스트하는 데 드는 비용이 비교된다.

### 1.5 비용최소화

1. 수행: Azure 가격 및 TCO 계산기를 사용하여 비용 분석 수행
2. 모니터링: Azure Advisor를 사용하여 사용량을 모니터링한다. 권장 사항을 구현한다.
3. 사용
    - 지출 한도를 사용한다. 무료 평가판 고객 및 일부 credit Azure 구독을 통해 사용
    - Azure 예약 및 Azure 하이브리드 혜택(HUB)을 사용
4. 선택: 저렴한 위치 및 지역을 선택
5. 유지: 최신 Azure 고객 및 구독 혜택에 대한 정보를 숙지
6. 적용: 태그를 적용하여 비용 소유자를 식별, 사용량 소유자를 식별

### 1.6 Knowledge Check

Q. 테스트 팀에서 이 환경을 데이터베이스와 Azure에서 실행하는 데 드는 비용을 비교하려면 취해야 할 가장 적합한 첫 번째 단계는 무엇일까요?

1. 단지 테스트 환경일 뿐이니 환경을 스핀업하여 월말에 청구서를 확인합니다.
2. 클라우드에서 실행하는 비용이 데이터 센터에서 실행하는 비용과 같다고 가정합니다.
3. 총 소유 비용 계산기 실행

Q. 개발 팀이 동시에 너무 많은 가상 머신을 프로비저닝하지 않도록 하는 가장 좋은 방법은 무엇일까요?

1. 아무 작업도 하지 않습니다. 개발 팀이 필요한 것을 사용하도록 둡니다.
2. 개발 팀의 Azure 구독에 지출 한도를 적용합니다.
3. 개발 팀 리드에게 구두로 예산을 알려주고 초과 사용분에 대한 책임을 지게한다.

Q. 다음 중 테스터가 근무하지 않는 주말에 테스트 팀이 가상 머신 비용을 절감할 가장 효율적인 방법은 무엇일까요?

1. 주말이 되기 전 가상 머신을 삭제하고 다음 주가 되면 새로 만듭니다.
2. 사용 중이 아닌 가상 머신을 할당 취소합니다.
3. 모든 것이 실행되도록 둡니다. Azure 사용한 CPU 시간에 대해서만 요금을 청구합니다.

Q. Dev 및 테스트 환경의 리소스 비용은 각각 서로 다른 부서에서 지불합니다. 부서를 기준으로 비용을 분류하는 가장 좋은 방법은 무엇일까요?

1. 각 가상 머신에 해당 청구 부서를 식별하는 태그를 적용합니다.
2. 부서 간 비용을 균등하게 분할
3. 각 팀의 리소스를 나열한 스프레드시트를 만들어 관리

> SHOUT OUT TO  
> [[MS Learn] Azure 비용 계획 및 병합하기](https://docs.microsoft.com/ko-kr/learn/modules/plan-manage-azure-costs/)
> [Microsoft Azure Virtual Training Day: Fundamentals](http://www.microsoft.com/ko-kr/events/training-days)

### 1.7 Answer

[3]

[2]

[2]

[1]