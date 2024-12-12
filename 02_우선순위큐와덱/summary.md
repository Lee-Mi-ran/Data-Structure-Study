# 우선순위큐(Priority Queue)

- 정의: 큐와 달리 들어오는 순서 상관 없이 우선순위가 높은 데이터가 먼저 나가는 자료구조 → 같은 우선순위를 가진다면, 먼저 들어온 원소를 처리, 오름차순으로 데이터 꺼내지는 게 default
- 힙을 사용하여 구현하는 것이 최적
- 아래 힙 내용 확인
- 파이썬에서의 우선순위큐

  ```python
  # 클래스 import 및 선언
  from queue import PriorityQue
  queue = PriorityQueue()

  # 우선순위 큐는 사이즈 제한 X -> 필요한 경우 maxsize 설정
  # queue = PriorityQueue(maxsize=10)

  # 원소추가
  queue.put(4)
  queue.put(8)
  queue.put(6)

  # 원소제거(반환)
  print(queue.get()) # 4
  print(queue.get()) # 6
  print(queue.get()) # 8
  ```

- 우선순위 큐 구현 방식
  - 리스트
  - PriorityQue
  - 힙: 제일 속도가 빠름

# 힙

- 우선순위 큐를 구현하기 위한 자료구조
- 완전 이진트리 기반 - 최소힙
  ![image.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbsWAKX%2FbtrWbLf60Nf%2FriWUYLo8p7X5l050QpKz90%2Fimg.png)
  (출처: https://tmdrnr96.tistory.com/32)
- heapq모듈 사용

  ```python
  import heapq

  heap = []

  heapq.heappush(heap, data)
  heapq.heappop(heap) # 가장 작은 항목을 pop

  ```

- 연습문제
  - 백준(과제)
    [문제](https://www.acmicpc.net/problem/13904)

# 덱

- 양쪽에서 삽입과 삭제가 가능
- 스택과 큐 연산을 모두 지원하는 자료구조
  ![image.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FqWlY0%2FbtqvP4M94Fk%2FUUNygvQM061nj5s0qkhXuK%2Fimg.jpg)
  (출처: https://jjudrgn.tistory.com/15)
- 소스코드

  ```python
  from collections import deque

  deq = deque([1,2,3,4])

  # 양쪽 삽입
  deq.appendleft(-10)
  deq.append(10)

  # 양쪽 삭제
  deq.pop()
  deq.popleft()
  ```

## 같이 풀 문제

- 위 문제와 동일
