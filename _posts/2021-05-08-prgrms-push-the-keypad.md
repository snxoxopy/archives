---
title:  "[Python] PRGRMS_67256 키패드 누르기"
excerpt: "https://programmers.co.kr/learn/courses/30/lessons/67256"
toc: true
toc_sticky: true
toc_label: "Contents"

sidebar:
  - title: "solved.ac"
    image: https://camo.githubusercontent.com/79fcbf056ec4786197f8a86132aeb99b66bde335982a6b7a41822dd3c122c912/687474703a2f2f6d617a617373756d6e6964612e7774662f6170692f6d696e692f67656e65726174655f62616467653f626f6a3d736e6f6f5f7079
    text: "![solved.ac snoo_py](https://camo.githubusercontent.com/f3f9383373ad9de51bd943325a32385a6790abaff724d37a55ede446710a80a0/687474703a2f2f6d617a617373756d6e6964612e7774662f6170692f76322f67656e65726174655f62616467653f626f6a3d736e6f6f5f7079)"

author_profile: true
categories:
  - algorithm
tags:
  - programmers
  - implementation
---

## 문제

[코딩테스트 연습 - 키패드 누르기](https://programmers.co.kr/learn/courses/30/lessons/67256)

## 결과

```python
테스트 1 〉	통과 (0.00ms, 10.2MB)
테스트 2 〉	통과 (0.01ms, 10.2MB)
테스트 3 〉	통과 (0.01ms, 10.3MB)
테스트 4 〉	통과 (0.00ms, 10.3MB)
테스트 5 〉	통과 (0.01ms, 10.2MB)
테스트 6 〉	통과 (0.01ms, 10.3MB)
테스트 7 〉	통과 (0.02ms, 10.3MB)
테스트 8 〉	통과 (0.04ms, 10.2MB)
테스트 9 〉	통과 (0.03ms, 10.2MB)
테스트 10 〉	통과 (0.03ms, 10.3MB)
테스트 11 〉	통과 (0.08ms, 10.3MB)
테스트 12 〉	통과 (0.06ms, 10.3MB)
테스트 13 〉	통과 (0.11ms, 10.3MB)
테스트 14 〉	통과 (0.26ms, 10.2MB)
테스트 15 〉	통과 (0.84ms, 10.3MB)
테스트 16 〉	통과 (0.67ms, 10.3MB)
테스트 17 〉	통과 (1.22ms, 10.3MB)
테스트 18 〉	통과 (1.57ms, 10.2MB)
테스트 19 〉	통과 (1.20ms, 10.3MB)
테스트 20 〉	통과 (1.27ms, 10.2MB)
```

## 풀이

- 이전 번호 기억하기
    - stack
- 2, 5, 8, 0일 경우 최단 거리 구하기
    - abs(row_cur - row_prev) + abs(col_cur - col_prev)

## Code

```python
def solution(numbers, hand):
    answer = ''
    pos_r = [10]
    pos_l = [12]
    for number in numbers:
        if number == 0: number = 11
        if number % 3 == 1 and number <= 7: # left
            answer += "L"
            pos_l.append(number)
        elif number % 3 == 0 and number <= 9: #right
            answer += "R"
            pos_r.append(number)
        else:
            row_cur = (number - 1) // 3
            col_cur = (number - 1) % 3
            row_prev = (pos_l[-1] - 1) // 3
            col_prev = (pos_l[-1] - 1) % 3
            dist_l = abs(row_cur - row_prev) + abs(col_cur - col_prev)

            row_prev = (pos_r[-1] - 1) // 3
            col_prev = (pos_r[-1] - 1) % 3
            dist_r = abs(row_cur - row_prev) + abs(col_cur - col_prev)

            print('number, dist_l, dist_r', number, dist_l, dist_r)

            if dist_l < dist_r:
                answer += "L"
                pos_l.append(number)
            elif dist_r < dist_l:
                answer += "R"
                pos_r.append(number)
            else:
                if hand == "left":
                    answer += "L"
                    pos_l.append(number)
                else:
                    answer += "R"
                    pos_r.append(number)

    return answer
```

## Error

```python
def solution(numbers, hand):
    answer = ''
    pos_r = [10]
    pos_l = [12]
    for number in numbers:
        if number == 0: number = 11
        if number % 3 == 1 and number <= 7: # left
            answer += "L"
            pos_l.append(number)
        elif number % 3 == 0 and number <= 9: #right
            answer += "R"
            pos_r.append(number)
        else:
            diff_l, diff_r = 0, 0
            norm_prev = (pos_l[-1] - 1) // 3 + 1
            norm_cur = (number - 1) // 3 + 1
            if norm_prev != norm_cur:
                diff_l = 1 if abs(pos_l[-1] - number) == 3 else abs(number - norm_prev)
            else:
                diff_l = abs(pos_l[-1] - number)

            norm_prev = (pos_r[-1] - 1) // 3 + 1
            if norm_prev != norm_cur:
                diff_r = 1 if abs(pos_r[-1] - number) == 3 else abs(number - norm_prev)
            else:
                diff_r = abs(pos_r[-1] - number)
            #print('number, diff_l, diff_r', number, diff_l, diff_r)
            if diff_l < diff_r:
                answer += "L"
                pos_l.append(number)
            elif diff_r < diff_l:
                answer += "R"
                pos_r.append(number)
            else:
                if "left" in hand:
                    answer += "L"
                    pos_l.append(number)
                else:
                    answer += "R"
                    pos_r.append(number)

    return answer
```