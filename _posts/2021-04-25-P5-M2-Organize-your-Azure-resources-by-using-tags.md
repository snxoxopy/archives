---
title:  "[Cloud] P5_M2_Build a cloud governance strategy on Azure"
excerpt: Part5/Module2/Azure에서 클라우드 거버넌스 전략 빌드
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

## Module 5 - Learning objectives

After completing this module, you'll be able to:

- Make organizational decisions about your cloud environment by **using the Cloud Adoption Framework** for Azure.
- Define who can access cloud resources by using Azure **role-based access contro**l.
- **Apply a resource lock** to prevent accidental deletion of your Azure resources.
- **Apply tags** to your Azure resources to help describe their purpose.
- Control and audit how your resources are created by **using Azure Policy**.
- Enable governance at scale across multiple Azure subscriptions by **using Azure Blueprints**.

## Summary

- Azure RBAC(역할 기반 액세스 제어)를 사용하여 액세스 권한을 정의하는 역할을 만들 수 있습니다.
- 리소스 잠금을 통해 리소스를 실수로 삭제하거나 변경하는 것을 방지합니다.
- 리소스 태그는 리소스에 관한 추가 정보 또는 메타데이터를 제공합니다.
- Azure Policy는 리소스를 제어하거나 감사하는 정책을 만들고, 할당하고, 관리할 수 있는 Azure의 서비스입니다.
- Azure Blueprints를 사용하면 조직에 필요한 거버넌스 도구 및 표준 Azure 리소스의 반복 가능한 세트를 정의할 수 있습니다.

## 1. Accelerate your cloud adoption journey by using the Cloud Adoption Framework for Azure

### 1.1 What's in the Cloud Adoption Framework?

- 아래 stages로 구성됨

![https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/build-cloud-governance-strategy-azure/media/2-framework-stages.png](https://docs.microsoft.com/ko-kr/learn/azure-fundamentals/build-cloud-governance-strategy-azure/media/2-framework-stages.png)

### 1.2 Define you strategy

1. Define and document your motivations
2. Document business outcomes
3. Develop a business case
4. Choose the right first project

### 1.3 Make a plan

1. Digital estate: 클라우드로 마이그레이션할 계획인 기존 디지털 자산 및 워크로드의 인벤토리를 만듭니다.
2. Initial organizational alignment: 기술적 관점에서 적합한 사용자가 마이그레이션 작업에 참여하는지 확인
3. Skills readiness plan: 개인이 필요한 기술을 연마하는 데 도움이 되는 계획을 수립
4. Cloud adoption plan: 팀을 함께 공유 클라우드 채택 목표로 이끄는 포괄적인 계획을 수립

### 1.4 Ready you organization

1. Azure setup guide: 방문 영역을 만드는 데 사용해야 하는 도구와 방법을 숙지
2. Azure landing zone: 각 주요 영역을 지원하는 Azure 구독을 빌드하기 시작
3. Expand the landing zone: 운영, 거버넌스 및 보안 요구 사항을 충족하는지 확인
4. Best practices: 클라우드 마이그레이션 작업이 스케일링 및 유지가 가능하다는 것을 보장하는 입증된 권장 사례로 시작

### 1.5 Adopt the cloud

1. Migrate
    1. Migrate your first workload: 첫 번째 프로젝트를 클라우드에 배포
    2. Migration scenarios: 복잡한 마이그레이션 시나리오를 살펴보기
    3. Best practices: 권장되는 사례를 따르고 있는지 확인
    4. Process improvements: 더 적은 작업으로 마이그레이션 프로세스를 스케일링하는 방법을 식별
2. Innovate
    1. Business value consensus: 고객 요구 사항을 충족하는지 확인
    2. Azure innovation guide: 개발을 가속화하고 아이디어의 MVP(최소 기능 제품)를 빌드
    3. Best practices: 진행률이 권장 사례에 매핑되는지 확인
    4. Feedback loops: 고객에게 필요한 항목을 빌드 중인지 확인

### 1.6 Govern and manage your cloud environments

1. Govern
    1. Methodology: 전체 클라우드 거버넌스까지 증분 방식으로 진행
    2. Benchmark: 현재 상태와 이후 상태를 평가하고 프레임워크를 적용하기 위한 비전을 설정
    3. Initial governance foundation: 첫 번째 단계를 캡처하는 MVP 생성
    4. Improve the initial governance foundation: 명백한 위험을 해결하는 거버넌스 컨트롤을 반복적으로 추가
2. Manage
    1. Establish a management baseline: 환경의 모든 자산에 적용해야 하는 최소한의 도구 및 프로세스 세트 정의
    2. Define business commitments: 지원되는 워크로드를 문서화하고 각 워크로드에 대한 클라우드 관리 투자에 동의
    3. Expand the management baseline: 초기 관리 기준에서 반복할 권장 모범 사례를 적용
    4. Advanced operations and design principles: 높은 수준의 비즈니스 약정이 필요한 워크로드의 경우 복원력 및 안정성 약정을 제공하기 위해 더 자세한 아키텍처 검토

## 2. Create a subscription governance strategy

### 2.1 Billing

- 구독당 하나의 청구 보고서를 만들 수 있다.
- 부서 또는 프로젝트별로 구독을 구성하여 결제하는 것을 고려할 수 있다.

### 2.2 Access Control

- 모든 구독은 Azure Active Directory Tenant와 연결됨
- Tenant는 Administrators에게 Azure 역할 기반 액세스 제어를 사용
- 역할 기반 액세스 제어를 사용하여 정의된 역할을 통해 세분화된 액세스를 설정하는 기능을 제공

### 2.3 Subscription limits

- 구독에는 몇 가지 리소스 제한
    - ex) 구독당 최대 네트워크 Azure ExpressRoute 회로 수는 10개
- 한도를 초과해야 할 때 추가 구독 필요
    - If you hit a hard limit maximum, there's no flexibility to increase it

## 3. Control access to cloud resources by using Azure role-based access control

### 3.1 How is role-based access control applied to resources?

- A management group (a collection of multiple subscriptions): 관리 그룹 범위에서 사용자에게 소유자 역할을 할당하면 해당 사용자는 관리 그룹 내에서 모든 구독의 모든 항목을 관리할 수 있습니다.
- A single subscription: 구독 범위에서 그룹에 읽기 권한자 역할을 할당하면 해당 그룹의 멤버는 구독 내의 모든 리소스 그룹 및 리소스를 볼 수 있습니다.
- A resource group: 리소스 그룹 범위에서 애플리케이션에 기여자 역할을 할당하면 애플리케이션은 해당 리소스 그룹 내에서 모든 형식의 리소스를 관리할 수 있지만 구독 내의 다른 리소스 그룹은 관리할 수 없습니다.
- A single resource

### 3.2 When should I use Azure RBAC?

- 한 사용자는 구독의 VM을 관리하고 다른 사용자는 가상 네트워크를 관리하도록 허용
- 데이터베이스 관리자 그룹이 구독의 SQL 데이터베이스를 관리하도록 허용
- 사용자가 가상 머신, 웹 사이트, 서브넷 등 리소스 그룹의 모든 리소스를 관리하도록 허용
- 애플리케이션이 리소스 그룹의 모든 리소스에 액세스하도록 허용

### 3.3 How is Azure RBAC enforced?

- Azure Portal, Azure Cloud Shell, Azure PowerShell 및 Azure CLI에서 Resource Manager에 액세스
- Azure RBAC는 애플리케이션 또는 데이터 수준에서 액세스 권한을 적용하지 않습니다. 애플리케이션 보안은 애플리케이션에서 처리해야 합니다.
- 역할이 할당되면 RBAC는 읽기, 쓰기 또는 삭제와 같은 특정 작업을 수행하도록 허용 합니다.

### 3.4 Who does Azure RBAC apply to?

- IT Administrators: 모든 리소스에 대한 전체 제어 권한이 필요
- Backup and Disaster Recovery: 정기 백업 상태를 관리하고 데이터 또는 시스템 복구를 호출하는 작업을 담당
- Cost and Billing: 기술과 관련된 비용을 추적하고 보고
- Security Operations: 기술 관련 보안 인시던트를 모니터링하고 대응

### 3.5 How do I manage Azure RBAC permissions?

- Azure Portal의 액세스 제어(IAM) 창에서 관리

## 4. Prevent accidental changes by using resource locks

### 4.1 How do I manage resource locks?

- 리소스 잠금을 통해 리소스를 실수로 삭제하거나 변경하는 것을 방지
- Azure Portal, PowerShell, Azure CLI 또는 Azure Resource Manager 템플릿에서 리소스 잠금을 관리
- 리소스 잠금은 RBAC 권한에 관계 없이 적용

### 4.2 What levels of locking are available?

- CanNotDelete: 권한 있는 사용자가 리소스를 읽고 수정 가능, 잠금을 제거하지 않고는 삭제 불가
- ReadOnly: 권한 있는 사용자가 리소스 읽기 가능, 리소스를 삭제하거나 변경할 수 없음

### 4.3 How do I delete or change a locked resource?

- 잠금제거
- 리소스 소유자라 할지라도 차단된 활동을 수행하려면 먼저 잠금을 제거해야 한다.

### 4.4 Combine resource locks with Azure Blueprints

- Azure Blueprints는 클라우드 관리자가 실수로 리소스 잠금을 삭제할 경우를 위해 사용
- Azure 리소스 세트를 정의

### 4.5 Knowledge

Q. 일부 사용자가 각 환경에서 가상 머신을 제어하도록 허용하지만 동일한 리소스 그룹 또는 Azure 구독에서 네트워킹 및 기타 리소스를 수정하지 못하도록 방지하려면 어떻게 해야 하나요?

1. Azure RBAC을 통해 역할 할당을 만듭니다.
2. 리소스 사용을 감사하는 Azure Policy에서 정책을 만듭니다.
3. 환경을 별도 리소스 그룹으로 분할합니다.

> SHOUT OUT TO  
> [[MS Learn] Azure 역할 기반 액세스 제어를 사용하여 클라우드 리소스에 대한 액세스를 제어](https://docs.microsoft.com/ko-kr/learn/modules/build-cloud-governance-strategy-azure/4-control-access-azure-rbac)

## 5. Organize your Azure resources by using tags

- 태그는 리소스에 관한 추가 정보 또는 메타데이터를 제공
- 리소스를 분류법으로 논리적으로 구성
- 이름-값 쌍으로 구성
- 청구 정보를 합산하는데 유용

### 5.1 This metadata is useful for

- Resource management: 태그를 사용하면 특정 워크로드, 환경, 사업부 및 소유자와 연결된 리소스를 찾고 작업할 수 있습니다.
- Cost management and optimization: 태그를 사용하면 리소스를 그룹화하여 비용을 보고하고, 내부 비용 센터를 할당하고, 예산을 추적하고, 예상 비용을 예측할 수 있습니다.
- Operations management: 태그를 사용하면 비즈니스에 대한 가용성의 중요도에 따라 리소스를 그룹화할 수 있습니다. 이렇게 그룹화하면 SLA(서비스 수준 계약)를 작성하는 데 도움이 됩니다.
    - SLA는 여러분과 사용자 간의 작동 시간 또는 성능 보장
- Security: 태그를 사용하면 보안 수준(예: 퍼블릭 또는 기밀)을 기준으로 데이터를 분류
- Governance and regulatory compliance
    - 태그를 사용하면 거버넌스 또는 규정 준수 요구 사항(예: ISO 27001)에 부합하는 리소스를 식별
    - 태그는 표준 적용 작업의 일부일 수도 있습니다. 예를 들어 모든 리소스에 소유자 또는 부서 이름으로 태그를 지정
- Workload optimization and automation: 태그를 통해 복잡한 배포에 참여하는 모든 리소스를 시각화
    - ex) 연결된 워크로드 또는 애플리케이션 이름으로 리소스에 태그를 지정하고 Azure DevOps와 같은 소프트웨어를 사용하여 해당 리소스에서 자동화된 작업을 수행

### 5.2 How do I manage resource tags?

- tags 추가, 수정, 삭제: PowerShell, Azure CLI, Azure Resource Manager 템플릿, REST API 또는 Azure Portal에서 가능
- tags 지정 규칙 적용, 리소스가 부모 리소스 그룹과 동일한 태그를 상속하는지 확인: Azure Policy


### 5.3 An example tagging structure

|Name|값|
|:---|:---|
|AppName|리소스가 속한 애플리케이션의 이름입니다.|
|CostCenter|내부 비용 센터 코드입니다.|
|소유자|리소스를 담당하는 비즈니스 소유자의 이름입니다.
|환경|"Prod", "Dev" 또는 "Test"와 같은 환경 이름입니다.|
|영향|"중요 업무용", "높은 영향", "낮은 영향" 등의 비즈니스 운영에 대한 리소스의 중요도입니다.|

### 5.4 Knowledge Check

Q. 각 Azure 리소스가 속한 청구 부서를 식별하는 가장 좋은 방법은 무엇인가요?

1. 스프레드시트에서 리소스 사용을 추적합니다.
2. 배포를 별도 Azure 구독으로 분할합니다. 여기서 각 구독은 자체 청구 부서에 속합니다.
3. 연결된 청구 부서를 포함하는 각 리소스에 태그를 적용합니다.

> SHOUT OUT TO  
> [[MS Learn] 태그를 사용하여 Azure 리소스 구성](https://docs.microsoft.com/ko-kr/learn/modules/build-cloud-governance-strategy-azure/7-organize-resource-tags)

### 5.5 Answer

[3]

- Azure Policy에서 조직 표준을 적용하고 규정 준수 여부를 대규모로 평가 가능
- Azure Policy에서 규제 준수, 보안, 비용, 관리 기능을 통해 리소스를 통제하고 일관성을 유지

### 6.1 How does Azure Policy define policies?

- Azure Policy는 리소스를 제어하거나 감사하는 정책을 만들고, 할당하고, 관리할 수 있는 서비스
- Azure Policy를 사용하면 ‘이니셔티브’라는 개별 정책 및 관련 정책 그룹을 둘 다 정의
- Azure Policy는 리소스를 평가하고 사용자가 만든 정책을 준수하지 않는 리소스를 강조 표시
- Azure Policy는 정책 미준수 리소스가 생성되지 않게 할 수도 있습니다.
- Azure Policy에는 스토리지, 네트워킹, 컴퓨팅, Security Center 및 모니터링과 같은 범주에서 사용할 수 있는 다양한 기본 정책과 이니셔티브 정의가 제공
    - ex) VM(가상 머신)의 특정 SKU(Stock Keeping Unit) 크기만 사용할 수 있도록 하는 정책을 정의한다고 가정, 해당 정책을 사용하도록 설정하면 새 VM을 만들거나 기존 VM의 크기를 조정할 때 해당 정책이 적용됩니다. 또한 Azure Policy는 환경에 있는 모든 현재 VM을 평가

### 6.2 Azure Policy in action

1. Create a policy definition
    - Allowed virtual machine SKUs: 조직에서 배포할 수 있는 VM SKU 세트를 지정가능
    - Allowed locations: 조직에서 리소스를 배포할 때 지정할 수 있는 위치를 제한 가능
    - MFA should be enabled on accounts with write permissions on your subscription: 계정 또는 리소스 위반을 방지하려면 쓰기 권한이 있는 모든 구독 계정에 대해 MFA(Multi-Factor Authentication)를 사용하도록 설정
    - CORS should not allow every resource to access your web applications: . 보안상 이유로 최신 웹 브라우저는 기본적으로 사이트 간 스크립팅을 제한합니다. 이 정책은 필요한 도메인만 웹앱과 상호 작용하도록 허용
        - CORS(원본 간 리소스 공유)는 한 도메인에서 실행되는 웹 애플리케이션이 다른 도메인의 리소스에 액세스할 수 있게 해주는 HTTP 기능
    - System updates should be installed on your machines
        - Azure Security Center가 서버에서 누락된 보안 시스템 업데이트를 추천 가능
2. Assign the definition to resources
    - 정책 정의를 구현하려면 리소스에 정의를 할당
    - ‘정책 할당’은 특정 범위 내에서 발생하는 정책 정의
    - 정책 할당은 해당 범위 내 모든 자식 리소스에 상속
    - 정책 할당에서 제외해야 하는 특정 자식 리소스가 있는 경우 정책 할당에서 하위 범위를 제외 가능
3. Review the evaluation results
    - 정책 평가는 시간당 한 번 정도 수행
    - 정책 정의를 변경하고 정책 할당을 만들면 해당 정책은 시간 내에 리소스에 대해 평가

### 6.3 What are Azure Policy initiatives?

- Azure Policy Initiatives는 관련 정책을 하나의 세트로 그룹화하는 방법
- Initiatives 정의는 더 큰 목표에 대한 규정 준수 상태를 추적하는 데 도움이 되는 모든 정책 정의를 포함
- Initiatives에는 다음 정책 정의가 포함
    - Security Center에서 암호화되지 않은 SQL Database 모니터링
    - Security Center에서 OS 취약성 모니터링
    - Security Center에서 누락된 Endpoint Protection 모니터링

### 6.4 Knowledge Check

Q, 팀이 비용 효과적인 가상 머신 SKU 크기만 배포하도록 하는 가장 좋은 방법은 무엇인가요?

1. Azure Policy에서 허용되는 SKU 크기를 지정하는 정책을 만듭니다.
2. 정기적으로 배포를 수동으로 검사하여 사용되는 SKU 크기를 확인합니다.
3. 허용되는 가상 머신 SKU 크기를 정의하는 Azure RBAC 역할을 만듭니다.

> SHOUT OUT TO  
[[MS Learn] Azure Policy를 사용하여 리소스 제어 및 감사](https://docs.microsoft.com/ko-kr/learn/modules/build-cloud-governance-strategy-azure/8-control-audit-resources-azure-policy)

### 6.5 Answer

[1]

정책을 사용하도록 설정한 후 새 가상 머신을 만들거나 기존 가상 머신의 크기를 조정할 때 해당 정책이 적용됩니다. 또한 Azure Policy는 환경에 있는 모든 현재 가상 머신을 평가합니다.

Azure RBAC를 사용하여 액세스 권한을 정의하는 역할을 만들 수 있지만 허용되는 가상 머신 SKU 크기를 정의할 수는 없습니다.

## 7. Govern multiple subscriptions by using Azure Blueprints

- Azure Blueprints는 새 환경을 빠르게 구축하고 설정하게 한다.
- 개발 팀은 Resource를 빠르게 개발하여 제공하기 위해 Networking 등의 기본 제공 구성 요소 집합을 사용하여 조직 규정을 준수하면서 신뢰할 수 있는 환경을 신속하게 구축할 수 있다.
- 아래 내용의 배포를 orchestration
    - Role assignments
    - Policy assignments
    - Azure Resource Manager templates
    - Resource groups

### 7.1 Azure Blueprints in action

1. Create an Azure blueprint.
2. Assign the blueprint.
3. Track the blueprint assignments.

### 7.2 What are blueprint artifacts?

- Artifacts: Blueprint 정의의 각 구성요소

### 7.3 How will Tailwind Traders use Azure Blueprints for ISO 27001 compliance?

- ISO 27001: 국제 표준화 기구에서 게시한 IT 시스템의 보안에 적용되는 표준
- Azure Blueprints에는 ISO 27001과 관련된 몇 가지 기본 제공 청사진 정의
- 템플릿에서 ISO 27001 청사진을 실행할 때 생성되는 아티팩트

![https://docs.microsoft.com/en-gb/learn/azure-fundamentals/build-cloud-governance-strategy-azure/media/10-iso-27001-shared-blueprint.png](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/build-cloud-governance-strategy-azure/media/10-iso-27001-shared-blueprint.png)