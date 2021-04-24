---
title:  "[Cloud] P2_M3_Explore Azure Storage services"
excerpt: Part2/Module3/Azure Storage 서비스 살펴보기
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

After completing this module, you'll be able to describe the benefits and usage of:

- Azure Blob Storage
- Azure Disk Storage
- Azure Files Storage
- Azure Blob Access tiers

# 1. Azure Storage account fundamentals

## 1.1 Azure Storage

- A service that you can use to store files, messages, tables, and other types of information
- Websites, mobile apps, desktop applications, and many other types of custom solutions can read data from and write data to Azure Storage.
- Used by infrastructure as a service virtual machines, and platform as a service cloud services.
- Azure VMs use Azure Disk Storage to store virtual disks.
- However, you can't use Azure Disk Storage to store a disk outside of a virtual machine.

## 1.2 Create storage account

- To begin using Azure Storage, you first create an Azure Storage account to store your data objects.

# 2. Disk storage fundamentals

## 2.1 Disk Storage

- Provides disks for Azure virtual machines
- Applications and other services can access and use these disks as needed
- Allows data to be persistently stored and accessed from an attached virtual hard disk

## 2.2 Disks

- Come in many different sizes and performance levels
- Come from solid-state drives (SSDs) to traditional spinning hard disk drives (HDDs)
- Come with varying performance tiers

# 3. Azure Blob storage fundamentals

## 3.1 Azure Blob Storage (Container Storage)

- An object storage solution for the cloud
- Can store massive amounts of data, such as **text or binary data**
- Is unstructured, meaning that there are no restrictions on the kinds of data it can hold
- Can manage thousands of simultaneous uploads, massive amounts of video data, constantly growing log files
- Can be reached from anywhere with an internet connection

## 3.2 Ideal for

- Serving images or documents directly to a browser
- Storing files for distributed access
- Streaming video and audio
- Storing data for backup and restore, disaster recovery, and archiving
- Storing data for analysis by an on-premises or Azure-hosted service
- Storing up to 8 TB of data for virtual machines

![https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-storage-fundamentals/media/account-container-blob.png](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-storage-fundamentals/media/account-container-blob.png)

## 3.3 Knowledge Check

Q. 비디오 이미지와 같은 대량의 비구조적 데이터를 저장하는 데 최적화 된 스토리지는?

1. Blob
2. 파일
3. 큐


Q. Azure Storage에서 blob으로 이미지 파일을 공유하기 위해 수행해야 하는 첫 번째 단계는 무엇인가요?

1. Image를 저장할 Azure Storage Container를 만듭니다.
2. Azure Storage 계정 만들기
3. Image 파일을 업로드하고 Container를 만듭니다.
4. SAS Token을 사용하여 Image에 대한 접근을 제한합니다.



Q. 백업 및 복원, 재해 복구, 보관을 위해 데이터를 저장하는 데 적합한 Azure Storage 옵션은 무엇인가요?

1. Azure Files Storage
2. Azure Disk Storage
3. Azure Blob Storage

> SHOUT OUT TO
>
>[[MS Learn] Azure Blob Storage 기본 사항](https://docs.microsoft.com/ko-kr/learn/modules/azure-storage-fundamentals/azure-blob-container-storage)

## 3.4 Answer

[1]

[2]

[3]

# 4. Azure Files fundamentals

## 4.1 Azure File shares

- Azure Files offers fully managed file shares in the cloud
- File shares in the cloud that are accessible via the industry standard Server Message Block(SMB) and Network File System (preview) protocols
- File shares can be mounted concurrently by cloud or on-premises deployments of Windows, Linux, and macOS

## 4.2 What do Azure Files offer

- Applications running in Azure virtual machines or cloud services can mount a file storage share to access file data
- Any number of Azure virtual machines or roles can mount and access the file storage share simultaneously
- Share files anywhere in the world, diagnostic data, or application data sharing
- Migrate applications that share data to Azure. The part of applications should work with minimal changes if you mount the Azure file share to the same drive letter that the on-premises application uses.
- Store configuration files on a file share and access them from multiple VMs
- Write data to a file share, and process or analyze the data later
- the SMB protocol ensures the data is encrypted in transit.
- You can access the files from anywhere in the world, by using a URL that points to the file.
- You can use Shared Access Signature (SAS) tokens to allow access to a private asset for a specific amount of time.

    ![https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-storage-fundamentals/media/sas-storage-uri.png](https://docs.microsoft.com/en-gb/learn/azure-fundamentals/azure-storage-fundamentals/media/sas-storage-uri.png)

# 5. Understanding Blob access tiers

## 5.1 The available access tiers

- Hot access tier: Optimized for storing data that is accessed frequently.
- Cool access tier: Optimized for data that is infrequently accessed and stored for at least 30 days.
- Archive access tier: Appropriate for data that is rarely accessed and stored for at least 180 days, with flexible latency requirements.

## 5.2 Considerations apply to the different access tiers

- Only the hot and cool access tiers can be set at the account level. The archive access tier isn't available at the account level.
- Hot, cool, and archive tiers can be set at the blob level, **during upload or after upload.**
- Data in the cool access tier can tolerate slightly lower availability, but still requires high durability, retrieval latency, and throughput characteristics similar to hot data. For cool data, a slightly lower availability service-level agreement (SLA) and higher access costs compared to hot data are acceptable trade-offs for lower storage costs.
- Archive storage stores data offline and offers the lowest storage costs, but also the highest costs to rehydrate and access data.

