---
title:  "[R] Data 수정하기 및 변수명 바꾸기"
excerpt: Doit R p91 ~ p110
toc: True
toc_sticky: True
toc_label: "Contents"
sidebar:
  nav: "docs"
categories:
  - data_science
tags:
  - R
---

## 변수 종류

### 1. 이산형(Discrete)

1. 명목형 변수
2. 순위형 변수

### 2. 연속형(Continous)

1. 간격형 변수
2. 비율형 변수


##  조건 파생 변수

조건문을 이용해 연속형 data를 이산형, 범주형 data로 바꿈

```R
> df_mpg$test <- ifelse(df_mpg$total >= 20, "pass", "fail")
> head(df_mpg, 20)
   manufacturer              model
1          audi                 a4
2          audi                 a4
3          audi                 a4
4          audi                 a4
5          audi                 a4
6          audi                 a4
7          audi                 a4
8          audi         a4 quattro
9          audi         a4 quattro
10         audi         a4 quattro
11         audi         a4 quattro
12         audi         a4 quattro
13         audi         a4 quattro
14         audi         a4 quattro
15         audi         a4 quattro
16         audi         a6 quattro
17         audi         a6 quattro
18         audi         a6 quattro
19    chevrolet c1500 suburban 2wd
20    chevrolet c1500 suburban 2wd
   displ year cyl      trans drv
1    1.8 1999   4   auto(l5)   f
2    1.8 1999   4 manual(m5)   f
3    2.0 2008   4 manual(m6)   f
4    2.0 2008   4   auto(av)   f
5    2.8 1999   6   auto(l5)   f
6    2.8 1999   6 manual(m5)   f
7    3.1 2008   6   auto(av)   f
8    1.8 1999   4 manual(m5)   4
9    1.8 1999   4   auto(l5)   4
10   2.0 2008   4 manual(m6)   4
11   2.0 2008   4   auto(s6)   4
12   2.8 1999   6   auto(l5)   4
13   2.8 1999   6 manual(m5)   4
14   3.1 2008   6   auto(s6)   4
15   3.1 2008   6 manual(m6)   4
16   2.8 1999   6   auto(l5)   4
17   3.1 2008   6   auto(s6)   4
18   4.2 2008   8   auto(s6)   4
19   5.3 2008   8   auto(l4)   r
20   5.3 2008   8   auto(l4)   r
   cty hwy fl   class total test
1   18  29  p compact  23.5 pass
2   21  29  p compact  25.0 pass
3   20  31  p compact  25.5 pass
4   21  30  p compact  25.5 pass
5   16  26  p compact  21.0 pass
6   18  26  p compact  22.0 pass
7   18  27  p compact  22.5 pass
8   18  26  p compact  22.0 pass
9   16  25  p compact  20.5 pass
10  20  28  p compact  24.0 pass
11  19  27  p compact  23.0 pass
12  15  25  p compact  20.0 pass
13  17  25  p compact  21.0 pass
14  17  25  p compact  21.0 pass
15  15  25  p compact  20.0 pass
16  15  24  p midsize  19.5 fail
17  17  25  p midsize  21.0 pass
18  16  23  p midsize  19.5 fail
19  14  20  r     suv  17.0 fail
20  11  15  e     suv  13.0 fail
> table(df_mpg$test)

fail pass 
 106  128
```

## Factor, 이산형 데이터

- 기본적으로 R에서 Factor는 이산형 데이터로 간주한다.
- 문자열은 자동으로 이산형으로 인식
- 하지만, Factor 형태로 지정해주는 것은 자동이 아님
- data 분석을 위해 이산형 데이터, factor 형 임을 인식하고 수동으로 바꾸는 것을 권장

```R
> df_mpg$test <- as.factor(df_mpg$test)
> str(df_mpg)
'data.frame':	234 obs. of  13 variables:
 $ manufacturer: chr  "audi" "audi" "audi" "audi" ...
 $ model       : chr  "a4" "a4" "a4" "a4" ...
 $ displ       : num  1.8 1.8 2 2 2.8 2.8 3.1 1.8 1.8 2 ...
 $ year        : int  1999 1999 2008 2008 1999 1999 2008 1999 1999 2008 ...
 $ cyl         : int  4 4 4 4 6 6 6 4 4 4 ...
 $ trans       : chr  "auto(l5)" "manual(m5)" "manual(m6)" "auto(av)" ...
 $ drv         : chr  "f" "f" "f" "f" ...
 $ city        : int  18 21 20 21 16 18 18 18 16 20 ...
 $ hwy         : int  29 29 31 30 26 26 27 26 25 28 ...
 $ fl          : chr  "p" "p" "p" "p" ...
 $ class       : chr  "compact" "compact" "compact" "compact" ...
 $ total       : num  23.5 25 25.5 25.5 21 22 22.5 22 20.5 24 ...
 $ test    
```

### qplot, 이산형 데이터
```R
> library(ggplot2)
> qplot(df_mpg$test)
```
![image](https://user-images.githubusercontent.com/36683439/116853314-cc3eaf80-ac30-11eb-9e3d-f2c79af46162.png)

```R
> df_mpg$grade <- ifelse(df_mpg$total >= 30, "A", ifelse(df_mpg$total >= 20, "B", "C"))
> qplot(df_mpg$grade)
```
![image](https://user-images.githubusercontent.com/36683439/116853584-47a06100-ac31-11eb-9356-bd671d5d7b62.png)

### 분석 도전 p123

```R
#Q1.
df_midwest <- as.data.frame(midwest)
str(df_midwest)

#Q2.
#rename(data, 새로운 변수명 = 이전 변수명)
df_midwest <- rename(df_midwest, total=poptotal)
df_midwest <- rename(df_midwest, asian=popasian)
str(df_midwest)

#Q3.
df_midwest$asianpt <- df_midwest$asian/df_midwest$total
hist(df_midwest$asianpt)

#Q4.
df_midwest$larg_small <- ifelse(mean(df_midwest$asianpt)<df_midwest$asianpt,"large","small")

#Q5.
table(df_midwest$larg_small)
qplot(df_midwest$larg_small)
```
