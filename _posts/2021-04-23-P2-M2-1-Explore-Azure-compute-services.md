---
title:  "[Cloud] P2_M2_1_Explore Azure compute services"
excerpt: Part2/Module2/Azure 컴퓨팅 서비스 살펴보기 (필수)
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

# Module 2 - Learning objectives

After completing this module, you'll be able to describe the benefits and usage of.

- Azure Virtual Machines
- Azure App Service
- Azure Container Instances
- Azure Kubernetes Service
- Azure Functions
- Windows Virtual Desktop

# 1. Overview of Azure compute services

- Cloud 기반의 Application을 실행하기 위한 주문형 컴퓨터 서비스
- **Disks, Processors, Memory, Networking, and OS와 같은 Computing Resources를 제공**
- 즉각적인 Resources 제공 (일반적으로 몇 분 또는 몇 초 이내)
- 사용 기간의 요금만 지불

|Disk Storage|Container Storage(Blob)|Azure Files|
|:-----------|:----------------------|:----------|
|- IaaS|- PaaS|- IaaS|
|- VMs, Applications 등의 Services가 접근하고 사용할 수 있는 Disks를 제공한다.|- Text 또는 Binary data와 같은 대량의 비구조적 Data 저장용으로 최적화되어있다.|- 표준 SMB Protocol을 사용하여 접근할 수 있는 고가용성 Network file shares를 설정한다.
|

## 1.1 Virtual Machines

- 완벽한 제어와 사용자 지정이 가능한 **IaaS**
- 물리적 Computer의 SW Emulation
    - *Emulation: 한 컴퓨터가 다른 컴퓨터처럼 똑같이 작동하도록 모방하는 것
- 포함된 기능
    - Processors
    - Memory
    - Storage
    - Networking

## 1.2 Container Instances and Kubernetes Service

- **PaaS**
- 운영 체제 관리 불필요
- 필요 시 적절하게 변경할 수 있는 가벼운 가상화 환경
- Container를 배포하고 관리하는데 사용할 수 있는 Compute resource
- 빠르게 동적으로 만들고, 생성, 확장 및 중지되도록 설계됨
- 유형
    - Azure Container Instances (ACI): VM 혹은 추가 Service를 관리할 필요 없이 실행할 수 있는
    - Azure Kubernetes Service (AKS): 분산 Architecture와 대량의 Container를 다루는데 적합한 Orchestration Service

## 1.3 Azure App Service

- **PaaS**
- 모든 Platform에서 실행되는 기업 수준의 Web, Mobile, API Apps 을 신속하게 build, deploy, scale
- 완전 관리형 Platform을 사용하여 인프라 유지 관리를 수행하는 동안 엄격한 성능, 확장성, 보안 및 규정 준수 요구 사항을 충족


## 1.4 Azure Functions (or *serverless computing*)

- Service를 실행하는 Code에 관해서만 관심이 있는 경우 유용
- 주로 REST 요청을 통한 어떤 event, timer 또는 다른 Azure service로부터 받은 메시지에 대한 응답으로 작업을 수행해야 하는 경우 사용
- 작업을 수초 이내 빠르게 완료

## 1.5 Windows Virtual Desktop

- Cloud에서 실행되는 Desktop 및 App Virtual Service이다.
- Gateway Server를 추가로 실행하지 않아도 전체 Desktop 가상화 환경을 생성할 수 있다.
- 호스트 풀을 무제한으로 게시하여 다양한 Workload를 처리할 수 있다.
- 풀링 방식, 다중 Session Resource를 활용하여 비용을 줄일 수 있다.

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