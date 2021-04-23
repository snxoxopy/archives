---
title:  "[Cloud] Understanding core Azure architectural components"
excerpt: Module 2 핵심 Azure 아키텍처 구성 요소 설명
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

- Azure 구독 및 관리 그룹
- Azure Resource, Resource Group, and Azure Resource Manager
- Azure 지역, 지역 쌍 및 가용성 영역

# 1. Azure Resource 구조 개요

## 1.1 Resource Manager

- 이 그룹은 여러 **구독에 대한 액세스**, 정책 및 규정 준수를 관리하는 데 도움이 됩니다. 관리 그룹에 속하는 모든 구독은 **관리 그룹에 적용되는 조건을 자동으로 상속**합니다.

## 1.3 Resource Group

- 리소스 그룹은 웹앱, 데이터베이스, 스토리지 계정과 같은 Azure 리소스가 배포되고 관리되는 논리적 컨테이너 역할을 합니다.

> SOUT OUT TO
>
> [Azure 구독, 관리 그룹, 리소스 개요 - Learn](https://docs.microsoft.com/ko-kr/learn/modules/azure-architecture-fundamentals/overview)

# 2. Azure 구독 및 관리 그룹

## 2.1 관리 그룹

- 모든 구독 및 관리 그룹은 각  Directory의 단일 계층 내에 위치합니다.
- 단일 Directory에서 10,000개의 관리 그룹이 지원 가능
- 관리 그룹 트리는 6개 수준까지 지원 가능리 그룹 트리는 6개 깊이 수준까지 지원 가능
- 각 관리 그룹 및 구독은 하나의 부모만 지원할 수 있습니다.
- 관리 그룹에 여러 Azure 구독이 포함될 수 있음 (여러 자식 요소)
- 관리 그룹에 적용된 조건을 구독이 상속함
- 정책을 적용하는 계층 구조 생성 가능하며 리소스 또는 구독 소유자는 이 보안 정책을 변경하여 거버넌스를 향상시킬 수 없음
- 관리 그룹 적용 예시
    - 프로덕션이라는 그룹에서 VM 위치를 미국 서부 지역으로 제한할 수 있습니다. 이 정책은 해당 관리 그룹의 하위 항목인 모든 기업계약 구독에 상속되고 해당 구독에 속한 모든 VM에 적용됩니다.
    - 여러 구독에 대한 사용자 액세스를 제공하여 관리 그룹에 하나만 할당하면 여러 구독에 RBAC를 스크립팅하지 않고 사용자가 필요한 모든 항목에 액세스할 수 있습니다.

## 2.2 Subscription

- 구독은 Azure 제품 및 서비스에 대한 인증되고 권한이 부여된 액세스를 제공
- Azure AD(Azure Active Directory) 또는 Azure AD 트러스트의 디렉터리에 있는 ID인 Azure 계정과 연결된 Azure 서비스의 논리적 단위
- 유형

    ![https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/azure-architecture-fundamentals/media/subscriptions.png](https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/azure-architecture-fundamentals/media/subscriptions.png)

    1. 청구경계
        - Azure 사용에 따른 Azure 계정 청구 방식을 결정
        - 청구 요구 사항에 따라 여러 개의 구독을 생성 가능
        - 각 구독에 대해 별도의 청구 보고서 및 송장을 생성
    2. 엑세스 제어 경계
        - 사용자가 특정 구독으로 프로비전할 수 있는 리소스 액세스를 관리 및 제어 가능
        - 구독 수준에서 액세스 관리 정책을 적용하며, 다른 조직 구조를 반영하기 위해 별도의 구독 생성 가능
        - 예) 비즈니스 내에서 고유한 Azure 구독 정책을 적용할 수 있는 서로 다른 부서가 있습니다. 이 청구 모델을 통해 특정 구독으로 사용자가 프로비저닝하는 리소스에 대한 액세스를 제어할 수 있습니다.

## 2.3 Exercises

Q. 여러 Azure 구독에서 거버넌스를 관리하는 데 사용할 수 잇는 것은 무엇입니까?

1. Azure Initiatives
2. 관리 그룹
3. 리소스 그룹

Q. 다음 중 Azure 계정에 연결된 Azure 서비스의 논리적 단위는 무엇입니까?

1. Azure 구독
2. 관리 그룹
3. 리소스 그룹


---

> SOUT OUT TO
[[MS Learn]구독 및 관리 그룹](https://docs.microsoft.com/ko-kr/learn/modules/azure-architecture-fundamentals/management-groups-subscriptions)

## 2.4 Answer

[2]

[1]


# 3. Azure Resource and Resource Manager

## 3.1 Resource

- Azure를 통해 사용할 수 있는 관리 가능한 항목
- 유형
    - VM
    - 스토리지 계정
    - 웹앱
    - 데이터베이스
    - 가상 네트워크

> SHOUT OUT TO
>
>[[MS Learn] Azure 구독 및 관리 그룹](https://docs.microsoft.com/ko-kr/learn/modules/azure-architecture-fundamentals/management-groups-subscriptions)

## 3.3 Resource Manager

- Azure용 배포 및 관리 서비스
- 액세스 제어, 잠금, 태그와 같은 관리 기능을 사용하여 배포 후에 리소스를 보호하고 구성
- 역할
    1. 사용자가 Azure 도구, API 또는 SDK에서 요청을 보내면 Resource Manager에서 요청을 받으면 요청을 인증하고 권한을 부여합니다.
    2. Resource Manager에서 요청된 작업을 수행하는 Azure 서비스에 요청을 보냅니다. 모든 요청이 동일한 API를 통해 처리되므로 모든 여러 도구에서 일관적인 결과 및 기능을 볼 수 있습니다.
- 이점
    - 스크립트가 아니라 선언적 템플릿을 통해 인프라를 관리
    - Resource Manager 템플릿은 Azure에 무엇을 배포하는지 정의하는 JSON 파일
    - 솔루션의 모든 리소스를 그룹으로 배포, 관리 및 모니터링
    - 개발 수명 주기 내내 솔루션을 다시 배포합니다(리소스가 일관된 상태로 배포됨을 확신할 수 있음).
    - 리소스가 올바른 순서로 배포되도록 리소스 간의 종속성을 정의합니다.
    - 모든 서비스에 액세스 제어를 적용합니다. RBAC가 기본적으로 관리 플랫폼에 통합되기 때문입니다.
    - 리소스에 태그를 적용하여 구독의 모든 리소스를 논리적으로 구성합니다.
    - 동일한 태그를 공유하는 리소스 그룹에 대한 비용을 확인하여 조직의 청구를 명확히 합니다.

## 3.4 Exercises

Q. 애플리케이션의 일부이고 동일한 수명 주기를 공유하는 모든 리소스는 모범 사례에 따라 동일한 무엇에 위치해야 합니까?

1. 가용성 집합
2. 지역
3. 리소스 그룹

Q. Azure Resource Manager 템플릿에 사용되는 형식은?

1. HTML
2. JSON
3. XML

Q. 다음 중 리소스 그룹에 적용되지 않는 기능은 무엇입니까?

1. 리소스는 한 리소스 그룹에만 있어야 합니다.
2. 역할 기반 액세스 제어를 리소스 그룹에 적용할 수 있습니다.
3. 리소스 그룹은 중첩할 수 있습니다.

Q. 다음 중 Azure 구독에 대한 올바른 설명은 무엇입니까?

1. 구독 없어도 Azure를 사용할 수 있습니다.
2. Azure 구독은 Azure 서비스의 논리적 단위 입니다.
3. 구독을 둘 이상 사용할 수 없습니다.

---

> SOUT OUT TO
[[MS Learn] Azure 리소스 및 Azure Resource Manager](https://docs.microsoft.com/ko-kr/learn/modules/azure-architecture-fundamentals/resources-resource-manager)

## 3.5 Answer

[3]

[2]

[3]

[2]

# 4. Azure 지역, 지역 쌍 및 가용성 영역

## 4.1 Azure 지역

- Region

    ![](https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/azure-architecture-fundamentals/media/regions-expanded.png#lightbox)

    - Azure는 전 세계 Cloud 공급자 중 140개 이상 국가내에 60개 이상의 지역에서 Service를 제공
    - 사용자가 선택할 수 있는 최소 단위
    - 사용자는 Region 내에서 어느 곳에 Resource가 생성되는지 알 수 없음
    - 전 세계에 위치한 Datacentre로 구성
    - 지도 상의 하나의 지리적 영억으로 적어도 한 개 이상의 Datacentre를 포함
    - 지역 안에 Datacentre를 서로 근접하게 위치하여 Network 대기시간이 짧음
    - **Data 보존 경계 내의 지역 보호**
    
## 4.2 Azure 지역 쌍

- Region Pairs
    - Region은 Disaster Recovery 목적으로 도움을 위한 Datacentre를 운영
    - 지역 쌍 간의 거리는 최소 300miles
    - 자동 복제 기능이 제공되는 Service가 존재
    - Service 중단 시, 해당 지역에 우선적으로 복구 진행
    - 가동 중지 시간을 최소화하기 위해 순차적으로 제공

        → Azure Update시, Paired Region은 동시에 Update 적용되지 않고 
    ![](https://ogu45.com/zbxe/files/attach/images/96/739/082/cff3f10950b5660535c079a4c30788ca.jpg)

## 4.3 Availability Options

- Region Pairs: Data 보존 경계 내의 지역 보호
- Region
    1. Single VM: Premium Storage 사용시 99.9% 연결 보장
    2. Availability Set

        ![https://ogu45.com/zbxe/files/attach/images/96/739/082/c14f47d927c170b068fd864ce6c531fd.jpg](https://ogu45.com/zbxe/files/attach/images/96/739/082/c14f47d927c170b068fd864ce6c531fd.jpg)

        - 99.95% 연결 보장
        - 유지 관리 혹은 하드웨어 오류 발생 시에도 응용 프로그램을 온라인 상태로 유지
            - Update Domain(UD): 예약된 유지관리, 성능 또는 보안 업데이트는 업데이트 도메인을 통해 순서가 정해짐
                - VM을 가용성 집합을 만들고 배포하게 되면, 두 VM이 절대로 동시에 죽지 않도록 분산배포 해줌(Fault Domain)
                - 물리적 장애를 회피시켜 줌
        - Fault domains(FD): 데이터 센터 내에서 여러 하드웨어에서 워크로드를 물리적으로 분리
            - 동시에 보안 업데이트가 진행되지 않도록 해 줌 (Update Domain)

        단, 데이터센터 자체가 망가졌을 경우, 가용성 집합으로는 대응이 불가능함.

    3. Availability Zone

        ![https://images.velog.io/images/snoo_py/post/16e95550-c8a5-4720-b0f1-1ed230ad16cb/image.png](https://images.velog.io/images/snoo_py/post/16e95550-c8a5-4720-b0f1-1ed230ad16cb/image.png)

        - 99.99% 연결보장
        - **전체 Datacentre 오류로 인한 가동 중지 시간이 발생해도 데이터 보호 가능**
        - 같은 지역 내의 Datacentre 분리 가능
        - 각 Datacentre에는 독립적인 전력/냉각/Networking 장치가 포함됨
        - 내부 광섬유망을 통해 연결부 광섬유망을 통해 연결


## 4.3 Exercises

Q. MS Azure 데이터 센터는 무엇을 기준으로 구성되고 제공됩니까?

1. Geography(지리)
2. Region(지역)
3. Zone(영역)

Q. 데이터와 애플리케이션을 가깝게 유지해야 하는 고객의 데이터 보존 및 규정 준수 요구사항을 충족하는 개념은?

1. 지리 (Geography)
2. 지역 (Region)
3. 영역 (Zone)

---

> SOUT OUT TO
[[MS Learn] Azure 지역, 가용성 영역 및 지역 쌍](https://docs.microsoft.com/ko-kr/learn/modules/azure-architecture-fundamentals/regions-availability-zones)
[[오구사십오] Azure 핵심 서비스](https://ogu45.com/zbxe/school/82739)

## 4.5 Answer

[2]
[1]

