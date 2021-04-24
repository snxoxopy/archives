---
title:  "[Cloud] P2_M4_Explore Azure networking services"
excerpt: Part2/Module4/Azure 네트워킹 서비스 살펴보기
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


# Module 4 - Learning Objectives

After completing this module, you'll be able to:

- Describe the core networking resources that are available in Azure.
- Describe the benefits and usage of Azure Virtual Network, Azure VPN Gateway, and Azure ExpressRoute.


# 1. Azure Virtual Network fundamentals

|Azure Virtual Network|VPN Gateway|Azure ExpressRoute|
|:--------------------|:----------|:-----------------|
|- Azure Virtual Network는 Azure resources가 다른 resources/internet/on-premises network와 통신할 수 있게 해준다.|- VPN Gateway는 공용 Internet을 통해 Azure Virtual Network와 On-premises 위치 간에 암호화된 Traffic을 전송하는데 사용한다.|- 연결 공급자가 제공하는 사설 연결을 통해 On-premises network를 Azure로 확장한다.|


## 1.1 What is Azure virtual networking?

- Azure 네트워크를 다른 Azure 리소스와 연결되는 리소스 집합
- 가상 네트워크를 사용하면 VM, 웹앱 및 데이터베이스와 같은 Azure 리소스가 서로 통신할 수 있고 인터넷의 사용자 및 온-프레미스 클라이언트 컴퓨터와 통신 가능
- 기능
    - Isolation and segmentation
    - Internet communications
    - Communicate between Azure resources
    - Communicate with on-premises resources
    - Route network traffic
    - Filter network traffic
    - Connect virtual networks

## 1.2 Connect virtual networks

- 네트워크 피어링을 사용하여 동일한 지역 또는 여러 지역에서 가상 네트워크를 서로 연결 가능
- Service End Points는 다음 PaaS에 대해 만들 수 있다.
    - Azure Storage
    - Azure SQL Database
    - Azure Cosmos DB
    - Azure SQL Data Warehouse
    - Azure Database for PostgreSQL
    - Azure for MySQL

    ![https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/local-or-remote-gateway-in-peered-virual-network.png](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/local-or-remote-gateway-in-peered-virual-network.png)
  
# 2. Azure Virtual Network settings

## 2.1 Create a virtual network

- Network name
- Address space: 가상 네트워크를 만든 후에 주소 공간을 추가할 수 있습니다.
- Subscription
- Resource group
- Location
- Subnet: 서브넷 이름은 문자나 숫자로 시작하고 문자, 숫자 또는 밑줄로 끝나야 합니다. 문자, 숫자, 밑줄, 마침표 또는 하이픈만 포함할 수 있습니다.
- DDoS protection
- Service endpoints

## 2.2 Define additional settings

- Network security group
- Route table

## 2.3 Configure virtual networks

- **Address spaces**: You can add additional address spaces to the initial definition.
- **Connected devices**: Use the virtual network to connect machines.
- **Subnets**: You can add additional subnets.
- **Peerings**: Link virtual networks in peering arrangements.

# 3. Azure VPN Gateway fundamentals

## 3.1 VPN gateways

- 가상 네트워크 게이트웨이의 유형
- 암호화된 터널을 사용
- **site-to-site**: 사이트 간 연결을 통해 온-프레미스 데이터 센터를 가상 네트워크에 연결
- **point-to-site**: 지점 및 사이트 간 연결을 통해 개별 디바이스를 가상 네트워크에 연결
- **network-to-network**: 네트워크 간 연결을 통해 가상 네트워크를 다른 가상 네트워크에 연결

## 3.2 Policy-vased VPNs

- IKEv1만 지원합니다.
- Use of static routing: 두 네트워크의 주소 접두사 조합에 따라 VPN 터널을 통해 트래픽을 암호화 및 암호를 해독하는 방법이 결정되는 정적 라우팅 을 사용
- VPN이 필요한 특정 시나리오에 사용

## 3.3 Route-based VPNs

- 가상 네트워크 간 연결
- 지점 및 사이트 간 연결
- 다중 사이트 연결
- Azure ExpressRoute 게이트웨이와 동시 사용
- IKEv2를 지원
- Uses any-to-any 트래픽 선택기 사용
- Can use dynamic routing protocols: 이 경우 원본 및 대상 네트워크는 정책 기반 VPN에 있거나 고정 라우팅을 사용하는 경로 기반 VPN에 있는 경우에도 정적으로 정의되지 않습니다. 대신, BGP(Border Gateway Protocol)와 같은 라우팅 프로토콜을 사용하여 동적으로 생성되는 네트워크 라우팅 테이블을 기반으로 데이터 패킷이 암호화

## 3.4 VPN gateway sizes

| SKU |Site-to-site/Network-to-network tunnels|Aggregate throughput benchmark|Border Gateway Protocol support|
|:---:|:-------------------------------------:|:----------------------------:|:-----------------------------:|
|Basic [See Note]|Maximum: 10|100 Mbps|Not supported|
|VpnGw1/Az|Maximum: 30|650 Mbps|Supported|
|VpnGw2/Az|Maximum: 30|1 Gbps|Supported|
|VpnGw3/Az|Maximum: 30|1.25 Gbps|Supported|

    * 기본 VPN 게이트웨이는 개발/테스트 워크로드에만 사용해야 합니다. 또한 게이트웨이를 제거하고 다시 배포하지 않으면 나중에 기본에서 VpnGW1/2/3/Az SKU로 마이그레이션하는 것은 지원되지 않습니다.

## 3.5 Required Azure and on-premises resources for VPN gateways

- Azure resources
    - Virtual network
    - GatewaySubnet
    - Public IP address
    - Local network gateway
    - Virtual network gateway
    - Connection
- On-premises resources
    - VPN 디바이스 (policy-based 또는 route-based VPN gateways 지원가능한)
    - 공용(인터넷 라우팅 가능) IPv4 주소

## 3.6 High-availability scenarios

- Active-Standby
- Active-Active
- ExpressRoute failover: VPN 게이트웨이를 ExpressRoute 연결의 보안 장애 조치(failover) 경로로 구성하는 것
- Zone-redundant gateways: VPN 게이트웨이 및 ExpressRoute 게이트웨이를 영역 중복 구성으로 배포

## 3.7 Knowledge Check

Q. Tailwind Traders에서는 지사 간에 보안 통신 터널을 만들려고 합니다. 다음 중 사용할 수 없는 기술은 무엇인가요?

1. 지점 및 사이트간 VPN
2. 암시적 FTP over SSL
3. Azure ExpressRoute
4. 사이트 간 VPN

Q. 다음 중 가상 네트워크를 연결하는 데 사용할 수 있는 옵션은 무엇인가요?

1. NAT(Nerwork Address Translation)
2. 다중 섀시 링크 집계
3. DHCP(Dynamic Host Configuration Protocol)
4. 가상 네트워크 피어링

> SHOUT OUT TO  
> [[MS Learn] Azure Virtual Network 설정](https://docs.microsoft.com/ko-kr/learn/modules/azure-networking-fundamentals/azure-virtual-network-settings)

## 3.8 Answer

[2]

[4]

# 4. Azure ExpressRoute fundamentals

## 4.1 Features and benefits of ExpressRoute

- **Layer 3 connectivity:** 연결 공급자를 통한 온-프레미스 네트워크와 Microsoft Cloud 간의 **3계층 연결**입니다. 임의의(IPVPN) 네트워크, 지점간 이더넷 연결, 이더넷 Exchange로 가상 간 연결을 통해 연결할 수 있습니다.
- **Microsoft 클라우드 서비스에 연결:** 모든 지정학적 지역에 걸쳐 **Microsoft 클라우드 서비스에 연결**합니다.
- **Global Reach:** ExpressRoute 프리미엄 추가 기능으로 모든 지역에 걸쳐 Microsoft 서비스에 **글로벌 연결**합니다.
- **Dynamic routing:** BGP를 통해 네트워크와 Microsoft 간 **동적 라우팅**
- **Built-in redundancy:** 높은 안정성을 위한 모든 피어링 위치의 **기본 중복성**입니다.
- 연결 가동 시간 SLA입니다.
- 비즈니스용 Skype에 대한 QoS 지원.

## 4.2 ExpressRoute connectivity models

![https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/azure-connectivity-models.png](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-networking-fundamentals/media/azure-connectivity-models.png)

1. CloudExchange 공동 배치
2. Point-to-Point:지점 간 이더넷 연결
3. Any-to-any: 임의 연결

## 4.3 Security considerations

- ExpressRoute는 On-premises infrastructure - Azure infrastructure 간의 Private 연결
- ExpressRoute를 사용하면 Data가 Public Internet을 통해 이동하지 않음
    - DNS Query, 인증서 해지 목록 확인 및 Azure Content Delivery Network 요청의 경우는 Public Internet을 통해 전송

## 4.4 Knowledge Check

Q. Tailwind Traders는 Azure ExpressRoute를 사용하여 온-프레미스 네트워크를 Microsoft 클라우드에 연결하려고 합니다. 다음 항목 중 Tailwind Traders에서 사용할 수 있는 ExpressRoute 모델이 아닌 것은 무엇인가요?

1. 임의 연결
2. 사이트 간 VPN(가상 사설망)
3. 지점 간 이더넷 연결
4. CloudExchange 공동배치

Q. 다음 옵션 중 ExpressRoute의 이점이 아닌 것은 무엇인가요?

1. 중복 연결
2. 일관된 네트워크 처리량
3. 암호화된 네트워크 통신
4. Microsoft Cloud Service에 접근

> SHOUT OUT TO  
> [[MS Learn] Azure ExpressRoute 기본 사항](https://docs.microsoft.com/ko-kr/learn/modules/azure-networking-fundamentals/express-route-fundamentals)

## 4.5 Answer

[2]

[3] ExpressRoute는 프라이빗 연결을 제공하지만 암호화되지는 않습니다.