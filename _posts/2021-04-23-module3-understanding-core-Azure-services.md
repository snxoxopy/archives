---
title:  "[Cloud] Understanding core Azure services"
excerpt: Module 3 Azure 컴퓨팅 서비스 살펴보기
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

# Module 3 - Learning objectives

After completing this module, you'll be able to describe the benefits and usage of.

- Azure Virtual Machines
- Azure App Service
- Azure Container Instances
- Azure Kubernetes Service
- Azure Functions
- Windows Virtual Desktop

# 1. Overview of Azure compute services

## 1.1 Azure Compute

- Cloud 기반의 Application을 실행하기 위한 주문형 컴퓨터 서비스
- Disks, Processors, Memory, Networking, and OS와 같은 Computing Resources를 제공
- 즉각적인 Resources 제공 (일반적으로 몇 분 또는 몇 초 이내)
- 사용 기간의 요금만 지불

## 1.2 Virtual Machines

- 물리적 Computer의 SW Emulation (Emulation: 한 컴퓨터가 다른 컴퓨터처럼 똑같이 작동하도록 모방하는 것)
- 완벽한 제어와 사용자 지정이 가능한 **IaaS**
- 포함된 기능
    - Processors
    - Memory
    - Storage
    - Networking

## 1.3 Container Instances and Kubernetes Service

- Container는 간단하고 가상화된 Application 환경
- 운영체제 관리를 불필요
- Container를 배포하고 관리하는데 사용할 수 있는 Compute resource
- 빠르게 동적으로 만들고, 생성, 확작 및 중지되도록 설계됨
- 유형
    - Azure Container Instances (ACI)
    - Azure Kubernetes Service (AKS)

## 1.4 Azure App Service

- 모든 Platform에서 실행되는 기업 수준의 Web, Mobile, API Apps 을 신속하게 build, deploy, scale
- 완전 관리형 Platform을 사용하여 인프라 유지 관리를 수행하는 동안 엄격한 성능, 확장성, 보안 및 규정 준수 요구 사항을 충족
- App Service is a platform as a service (PaaS) offering.

## 1.5 Azure Functions (or *serverless computing*)

- Service를 실행하는 Code에 관해서만 관심이 있는 경우 유용
- 주로 REST 요청을 통한 어떤 event, timer 또는 다른 Azure service로부터 받은 메시지에 대한 응답으로 작업을 수행해야 하는 경우 사용
- 작업을 수초 이내 빠르게 완료

## 1.6 Knowledge check

Q. 기본 플랫폼이나 인프라가 아닌 서비스를 실행하는 코드에만 중점을 두는 경우 사용해야 하는 서비스는 무엇입니까?

1. Azure App Service
2. Azure Container Instances
3. Azure Functions

Q. 몇 초 안에 응답해야 하는(주로 REST 명령을 통한) 이벤트에 대한 응답으로 작업을 수행하는 것이 중요한 경우 다음 중 어떤 서비스를 사용해야 합니까?

1. Azure Functions
2. Azure App Service
3. Azure Container Instances

> SHOUT OUT TO
>
> [[MS Learn] Azure 컴퓨팅 서비스 개요](https://docs.microsoft.com/ko-kr/learn/modules/azure-compute-fundamentals/overview)

## 1.7 Answer

[3]

[1]

- 해설 Azure App Service는 Azure Functions를 찾을 수 있는 Azure의 창

# 2. When to use Azure Virtual Machines

## 2.1 Virtual Machine and its Benefits

- 물리적인 Server 부족문제에 대한 해결방안
- IaaS를 가상화된 Server형식으로 제공
- VM에서 실행되는 모든 SW를 사용자 지정할 수 있습니다.
- Scale VMs in Azure: 사소한 작업을 위해 단일 VM을 실행 또는 VM을 함께 Group하여 고가용성, 확장성 및 중복성을 제공
    1. Virtual Machine Scale Sets
        - 동일한 VM sets 배포 및 관리하는 데 사용할 수 있는 Compute resource
        - 예) 천문학 이미지를 업로드하는 Website 운영시, 추가 서비스 구성 필요(Website VM의 여러 Instances간에 요청을 Routing)
            - VM Scale Sets은 해당 작업을 자동으로 수행
            - 몇 분 안에 많은 수의 VM을 중앙에서 관리, 구성 및 Update하므로 고가용성 Application을 제공
            - VM Instance의 수는 요구 또는 정의된 일정에 따라 자동으로 늘리거나 줄일 수 있습니다.
    2. Azure Batch
        - 수십, 수백 또는 수천 개의 VM으로 Scaling함으로써 대규모 병렬 및 고성능 컴퓨팅(HPC) 일괄 작업을 수행
- 다음이 필요할 때 선택하면 좋다.
    - OS의 완전한 제어 / Total control over the operating system
    - 사용자 지정 SW 실행하는 기능 / The ability to run custom software
    - 사용자 지정 Hosting 구성을 사용해야하는 경우 / To use custom hosting configurations
    - 물리적 Server에서 Cloud로 이동(lift and shift라고도 함)할 때 / Move to the cloud with VMs

## 2.2 Examples of when to use VMs

- During testing and development
    - 개발 담당자가 더 이상 필요하지 않을 때 VM을 손쉽게 삭제
- When running applications in the cloud
    - VM이 필요하지 않을 때 VM을 종료하거나 예기치 않은 수요 증가를 충족하기 위해 신속하게 VM을 시작하면 사용하는 Resource에 대해서만 요금을 지급
- When extending your datacentre to the cloud
    - SharePoint 같은 Application을 Local로 실행하는 대신 Azure VM에서 실행 가능
- During disaster recovery
    - IaaS 기반 접근 방식을 사용하여 막대한 비용을 절감
    - 기본 Datacentre에 오류가 발생한 경우 Azure에서 실행되는 VM을 만들어 중요한 Application을 실행한 다음 기본 Datacentre가 다시 작동하면 이를 종료 가능

## 2.3 Knowledge Check

Q. 동일한 가상머신 집합을 배포하고 관리하는 데 사용할 수 있는 Azure Compute 리소스는 무엇입니까?

1. 가상머신 가용성 집합
2. 가상머신 가용성 영역
3. 가상머신 확장 집합

> SHOUT OUT TO
>
> [[MS Learn] Azure Virtual Machines를 사용하는 경우](https://docs.microsoft.com/ko-kr/learn/modules/azure-compute-fundamentals/azure-virtual-machines)

## 2.4 Answer

[3]

# 3. When to use Azure Container Instances or Azure Kubernetes Service

## 3.1 What are containers?

- VM은 물리적 HW 투자 비용을 줄이는 좋은 방법이다. 하지만 단일 운영체제로 제한된다.
- 단일 Host machine에서 Application의 여러 Instances를 실행하려는 경우 Container를 사용하는 것이 좋다.
- 즉, VM과 달리 운영체제 관리는 포함되지 않는다.

## 3.2 Compare virtual machines to containers

- VM은 HW를 가상화, Container는 운영체제를 가상화한다.
- 환경을 완벽하게 제어해야하는 경우 VM → Complete control
- 환경을 완벽하게 제어할 필요 없는 경우 Container → Portability, Performance

## 3.3 Manage containers

- Containers는 Container orchestrator를 통해 관리
- Container orchestrator는 필요에 따라 Application Instances를 시작, 중지, scale out을 할 수 있다. 이를 Containers를 관리라고 말함
- 방법
    1. Azure Container Instances (ACI)
        - 가상 머신을 관리하거나 추가 서비스를 채택하지 않고도 Azure에서 컨테이너를 실행하는 가장 빠르고 간단한 방법
        - PaaS이며, 실행되는 Container를 Upload 하면 바로 수행할 수 있음
        - 소규모에 적합
    2. Azure Kubernetes Service (AKS)
        - A complete orchestration service for containers
            - Orchestration: 많은 Containers를 자동화, 관리 및 상호작용 하는 작업
        - Kubernetes에서 실행되는 응용 프로그램에서 Data 저장 및 검색을 위해 Azure Storage 또는 Azure Cosmos DB와 같은 Cloud 기반 저장소를 사용하는 것이 일반적
        - PaaS 이며, 오픈소스 K8s를 포팅한 것으로 복잡도가 상대적으로 높음
        - 큰 규모에 적합

## 3.4 Use containers in you solutions

- Website를 Containers로 분할
    1. Container#1 = Front end Hosting
    2. Container#2 = Back end Hosting 및 저장소
- 사용 예) Back end가 용량에 도달했지만 Front end와 저장소 부하가 크지 않은 경우 아래와 같이 할 수 있다.
    - 성능 향상을 위해 Back end를 별도로 scale
    - 다른 Storage 서비스를 사용
    - Application의 나머지 부분에 영향을 주지 않고 Storage container 변경
- What is a microservice?
    - 규모가 작고 잘 정의된 Web service
    - 일반적으로 조직에서는 각각의 단일 Business 기능을 구현하는 Microservice Architecture를 선택
    - 각 Service는 작은 개발 팀이 관리할 수 있는 개별 Code 기반이다.
    - 동일한 기술 stack, library, framework를 공유할 필요 없다.
        - 다른 Web services와의 결합이 느슨하다.
        - 각 Team 작업에 적합한 도구 선택 가능
        - 단일 개발 Team에서 Service를 Build, Test, Deploy 가능

# 4. When to use Azure App service

- Application을 가상화 할 수 있는 방법 중 하나 (VMs, Containers, App service)
- App Service는 Azure Functions를 찾을 수 있는 Azure의 창
- Website의 Front end를 Azure App Service에 배포
- Infrastructure를 관리할 필요 없이 원하는 Programming 언어로 Build, Host 가능
- Windows 및 Linux 지원
- PaaS

## 4.1 Azure App Service costs

- App Service 요금제에 따라 Host에 사용된 HW의 양이 결정
    - 예) 요금제에 따라 전용 또는 공유 HW 여부 및 Host용으로 예약된 Memory 양이 결정

## 4.2 Types of app services

- Web apps
    - ASP.NET, Core, Java, Ruby, Node.js, PHP 또는 Python을 사용한 Hosting web apps 지원
    - Windows, Linux 선택 가능
- API apps
    - 원하는 언어 및 Framework를 사용하여 REST 기반 Web API를 Build 가능
    - 생성된 apps는 HTTP 또는 HTTPS 기반의 Client에서 사용 가능
- WebJobs
    - Program 실행 가능(.exe, Java, PHP, Python, Node.js)
    - Script 실행 가능(.cmd, .bat, PowerShell, Bash)
    - 주로 Application logic의 일부분으로 Background에서 수행시 사용
- Mobile apps
    - To quickly build a back end for iOS and Android apps
    - Store mobile app data in a cloud-based SQL database
    - Send push notifications
    - Execute custom back-end logic in C# or Node.js

# 5. When to use Azure Functions

- 비용을 줄이기 위해 Application이 입력을 기다리는 시간에 요금을 지급하지 않기위해 사용
    - Application Logic이 Event 기반일 때 즉, 긴 시간 동안 Application이 특정 입력을 기다린 다음에야 처리를 수행할 때

## 5.1 Serverless Computing

- Abstraction of servers: 서버, 인프라 및 운영 체제의 추상화
- Event-driven scale: 크기 조정 및 성능이 자동으로 처리
- Micro-billing: 용량 설정 불필요, 사용한 Resources만큼 요금 청구
- 인프라는 사용자의 책임이 아님
- 구현 방식
    1. Azure Functions: 거의 모든 최신 언어로 코드를 실행할 수 있습니다.
    2. Azure Logic Apps: 웹 기반 디자이너에서 설계되며 코드를 작성하지 않고도 Azure 서비스에 의해 트리거된 논리를 실행할 수 있습니다.

## 5.2 Functions vs. Logic Apps

|     |Functions|Logic Apps|
|:---:|:--------|:---------|
|시스템 상태|일반적으로 상태 비저장이지만 Durable Functions가 상태를 제공합니다.|상태 저장입니다.|
|개발|코드 중심(명령적)입니다.|디자이너 중심(선언적)입니다.|
|연결|약 12개의 기본 제공 바인딩 형식. 사용자 지정 바인딩에 대한 코드를 작성합니다.|대규모의 커넥터 컬렉션. B2B 시나리오를 위한 엔터프라이즈 통합 팩입니다. 사용자 지정 커넥터를 빌드합니다.|
|작업|각 활동은 Azure 함수입니다. 활동 함수에 대한 코드를 작성합니다.|즉시 사용 가능한 작업의 대규모 컬렉션.|
|모니터링|Azure Application Insights.|Azure Portal, Log Analytics.|
|관리|REST API, Visual Studio.|Azure Portal, REST API, PowerShell, Visual Studio.|
|실행 컨텍스트|로컬로 또는 클라우드에서 실행할 수 있습니다.|클라우드에서만 실행합니다.|

# 6. When to use Windows Virtual Desktop

- 원격 작업자의 배포 프로세스를 신속하게 진행하는 방법
    - 관리자가 원격 작업자로 이루어진 새로운 개발 팀을 구축할 것을 요청
    - 신규 개발자는 Windows, Android 및 macOS 등 여러 운영 체제를 실행하는 고유한 컴퓨팅 디바이스를 보유

## 6.1 What is Windows Virtual Desktop?

- 클라우드에서 실행되는 데스크톱 및 애플리케이션 가상화 서비스
- 사용자는 모든 위치에서 클라우드 호스트 버전의 Windows를 사용가능
- Windows Virtual Desktop은 Windows, Mac, iOS, Android 및 Linux 같은 여러 디바이스에서 작동
- 최신 브라우저를 사용하여 Windows Virtual Desktop 호스트 환경에 액세스 가능

## 6.2 Why should you use Windows Virtual Desktop?

- 최적의 사용자 환경 제공
    - Gateway Server를 추가로 실행하지 않아도 전체 Desktop 가상화 환경 생성 가능
    - Host pull 무제한으로 게시하여 다양한 Workload 처리 가능
- 보안 강화

## 6.3 What are some key features of Windows Virtual Desktop?

- 간소화된 관리
- 성능 관리
- 다중 Session Windows 배포

## 6.4 How can you reduce costs with Windows Virtual Desktop?

- 사용자 라이선스 필요
- Computing 비용 절감
- Pulling 방식, 다중 Session Resources를 활용

## 6.5 Knowledge Check

Q. 회사에는 회사의 애플리케이션을 개발하는 데 있어 Windows 기반 소프트웨어를 사용해야 하는 원격 작업자 팀이 있지만, 팀 구성원은 MacOS, Linux 및 Windows와 같은 다양한 운영 체제를 사용하고 있습니다. 이 시나리오를 해결하는 데 도움이 되는 Azure 컴퓨팅 서비스는 무엇입니까?

1. Azure App Service
2. Windows Virtual Desktop
3. Azure Container Instances

> SHOUT OUT TO
>
> [[MS Learn] Windows Virtual Desktop을 사용하는 경우](https://docs.microsoft.com/ko-kr/learn/modules/azure-compute-fundamentals/windows-virtual-desktop)


## 6.6 Answer

[2]

- 해설
    - App Service는 클라우드에서 **웹앱**을 호스팅하는 서비스입니다.
    - Windows Virtual Desktop을 사용하여 팀 구성원은 클라우드에서 Windows를 실행할 수 있고, 회사의 요구 사항에 맞춰 필요한 애플리케이션에 액세스할 수 있습니다.
    - Azure Container Instances는 클라우드에서 **컨테이너화된 앱**을 호스트하는 데 사용합니다.