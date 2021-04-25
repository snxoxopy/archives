---
title:  "[Cloud] P5_M1_Secure access to your application by using Azure identity services"
excerpt: Part5/Module1/Azure ID 서비스를 사용하여 애플리케이션에 안전하게 액세스
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

- Explain the difference between **authentication** and **authorization**
- Describe bow **Azure AD** provides identity and access management
- Explain the role that single sing-on**(SSO)**, **multifactor authentication**, and **Conditional Access** play in managing user identity.

## 1. Compare authentication and authorization

### 1.1 What is authentication?

- The process of establishing **the identity of a person or service** that wants to access a resource
- Involves the act of challenging a party for legitimate credentials
- Provides the basis for **creating a security principal** for identity and access control

### 1.2 What is authorization?

- Establishes the user's identity
- The process of establishing **what level of access** an authenticated person or service has
- **Specifies** **what data** they're allowed to access and **what they can do** with it

### 1.3 How are authentication and authorization related?

- Once authenticated, authorization defines what kinds of applications, resources, and data that user can access.

![https://docs.microsoft.com/en-gb/learn/azure-fundamentals/secure-access-azure-identity-services/media/2-id-card-access.png](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/secure-access-azure-identity-services/media/2-id-card-access.png)

## 2. What is Azure Active Directory?

### 2.1 How does Azure AD compare to Active Directory?

- Active Directory
    - For on-premises environments
    - Provides an identity and access management service that's managed by your own organization
    - Microsoft doesn't monitor sign-in attempts.
- Azure AD
    - Cloud-based
    - Identity and access management service
    - Microsoft can help protect you by detecting suspicious sign-in attempts at no extra cost.

### 2.2 Who uses Azure AD?

- IT administrators
- App developers
- Users
- Online service subscribers

### 2.3 What services does Azure AD provide?

- Authentication
- Single sign-on
    - 한 가지 사용자 이름과 한 가지 암호만 기억하면 여러 Application 접근 가능
- Application management
- Device management

### 2.4 What kinds of resources can Azure AD help secure?

- External resources: Microsoft Office 365, the Azure portal, and thousands of other SaaS applications
- Internal resources: Apps on your corporate network and intranet, along with any cloud applications developed within your organization

### 2.5 What's single sign-on?

- Enables a user to **sign in one time** and use that credential to **access multiple resources** **and applications** from different providers

### 2.6 How can I connect Active Directory with Azure AD?

- **Azure AD** Connect synchronizes user identities between on-premises Active Directory and Azure AD.
- **Azure AD** makes you use features like SSO, multifactor authentication, and self-service password reset under both systems.
    - Self-service password 재설정 사용시 사용자가 알려진 손상된 암호를 사용할 수 없음

### 2.7 Knowledge Check

Q. 사용자가 여러 애플리케이션에 액세스하기 위해 인증해야 하는 횟수를 줄이려면 IT 부서에서 어떻게 해야 할까요?

1. SSO
2. 조건부 액세스
3. Multi-Factor Authentication

> SHOUT OUT TO  
[[MS Learn] Azure Active Directory란?](https://docs.microsoft.com/ko-kr/learn/modules/secure-access-azure-identity-services/3-what-is-azure-active-directory)

### 2.8 Answer

[1]

## 3. What are multifactor authentication and Conditional Access?

### 3.1 What's multifactor authentication?

During the sign-in process for an additional form of identification

- **Something the users knows**: e-mail 주소, 암호
- **Something the user has:** Mobile로 전송되는 Code
- **Something the user is**: 지문 또는 얼굴인식

### 3.2 What's Azure AD Multi-Factor Authentication?

- Azure Active Directory
    - Azure Active Directory Free
    - Azure Active Directory Premium
- Multifactor authentication for Office 365

### 3.3 What's Conditional Access?

- A tool that Azure Active Directory uses to allow (or deny) **access to resources based on identity signals**
    - Signals: who the user is, where the user is, and what device the user

![https://docs.microsoft.com/en-gb/learn/azure-fundamentals/secure-access-azure-identity-services/media/4-conditional-access-signal-decision-enforcement.png](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/secure-access-azure-identity-services/media/4-conditional-access-signal-decision-enforcement.png)

### 3.4 When can I use Conditional Access?

- Require multifactor authentication to access an application.
- Require access to services only through approved client applications.
- Require users to access your application only from managed devices.
- Block access from untrusted sources, such as access from unknown or unexpected locations.

### 3.5 Where is Conditional Access available?

- Azure AD Premium P1 or P2 license
- Microsoft 365 Business Premium license

### 3.6 Knowledge Check

Q. IT 부서에서 회사 소매점의 직원이 승인된 태블릿 디바이스에서만 회사 애플리케이션에 액세스할 수 있도록 하려면 어떻게 해야 하나요?

1. SSO
2. 조건부 액세스
3. Multi-Factor Authentication

Q. IT 부서에서 얼굴 인식과 같은 생체 인식 속성을 사용하여 배달원이 ID를 증명할 수 있게 하려면 어떻게 해야 하나요?

1. SSO
2. 조건부 액세스
3. Multi-Factor Authentication

> SHOUT OUT TO  
> [[MS Learn] 다단계 인증 및 조건부 액세스란?](https://docs.microsoft.com/ko-kr/learn/modules/secure-access-azure-identity-services/4-what-are-mfa-conditional-access)