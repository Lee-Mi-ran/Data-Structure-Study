> # 완전탐색 (브루트포스)

![완전탐색](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fv5S4y%2FbtrUfPpxr3u%2FuDMXztrX7RaNQrpKt5RqS1%2Fimg.png)
(출처 :https://siku314.tistory.com/82)
- 정의
    - 모든 가능한 경우의 수를 모두 탐색하여 최적의 결과를 찾는 탐색 알고리즘
    - 무식한게 답이다!
    - for문과 같은 반복문을 사용하여 다 돌림 -> 시간초과 에러날 경우 다른 방안을 생각해보아야함
    -> 이분(이진)탐색

 - 연습문제
    - https://school.programmers.co.kr/learn/courses/30/lessons/86491 (최소직사각형)

<br/>

> # 이진탐색 (이분탐색)
- 정의: 정렬된 데이터 리스트를 계속 둘로 나누어 해당하는 범위에서만 탐색되도록 하여 빠르게 원소를 탐색하는 알고리즘

![탐색비교](https://blog.kakaocdn.net/dn/erepNb/btrXooJgvCJ/dKGmKjkYnx7nHofWCrK5fk/img.gif) 
(출처:https://blog.penjee.com/binary-vs-linear-search-animated-gifs/)

- 파이썬의 이진탐색
    (출처: https://code-angie.tistory.com/3)
    ```python
    # 반복문 활용
    def binary_search(target, data):
        data.sort()
        start = 0
        end = len(data)-1

        while start <= end:
            mid = (start+end) // 2

            if data[mid] == target:
                return mid
            elif data[mid] > target:
                end = mid - 1
            else:
                start = mid + 1
            return
    
    # 재귀 활용
    def binary_search(target, start, end):
        if start > end:
            return -1
        
        mid = (start + end) // 2

        if data[mid] == target:
            return mid
        elif data[mid] > target:
            end = mid - 1


    ```