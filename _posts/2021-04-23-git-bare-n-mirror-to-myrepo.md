---
title:  "[Git] fork repository 잔디심기"
excerpt: 침착하게 잔디를 심어보자
toc: False
toc_sticky: False
toc_label: "Contents"
sidebar:
  nav: "docs"
categories:
  - blog
tags:
  - git
---

### 개발 환경

- Windows 10


### W5H1

- 언제: 2021-04-23
- 어디서: https://github.com/suzinee/archives
- 누가: snoo.py
- 무엇을: fork 저장소 옮기기
- 어떻게
  1. [GIT] 기존 저장소 이름 바꾸기
  2. [Terminal] git clone --bare 기존 저장소 주소
  3. [Terminal] git push --mirror 새로운 저장소 주소
- 왜: 기존 Commit을 유지하며 잔디를 심기 위해


### git clone --bare

- <directory> 를 생성하고 <directory>/.git 을 생성하는 대신에 <directory> 자체를 $GIT_DIR 로 만든다.
- 기존 저장소의 모든 태그, master(HEAD), next, pu, maint 지역 브랜치들을 얻어온다
- 모든 브랜치들은 이후 다시 fetching 을 기대하지 않도록 복사되고, 완전히 독립적으로 설정된다.
- 복제된 원격 저장소내의 모든 remote branches 와 refs 는 완전히 무시된다.


### 시행착오

AS-IS mirror 오 작동


1. 기존의 Remote repository 주소를 git clone bare 수행
2. Local Directory에 새로운 저장소를 생성
3. Terminal 경로를 Local Directory의 새로운 저장소로 이동 git push --mirror 수행

  ![](https://images.velog.io/images/snoo_py/post/abb3b81e-c738-4390-ac23-569947dc987c/image.png)

TO-BE mirror 정상 동작 확인
  
1. 기존의 Remote repository 주소를 git clone bare 수행
2. Terminal 경로를 기존에 작업하던 Local Directory에서 git push --mirror 수행

  ![](https://images.velog.io/images/snoo_py/post/d77a8b13-8d75-4834-869a-b387ea6dadf6/image.png)



> SHOUT OUT TO
> 
> [fork 해온 repository 잔디 심는 방법](https://soranhan.tistory.com/m/11)