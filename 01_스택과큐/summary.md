# 스택

![image.png](https://velog.velcdn.com/images/hyhy9501/post/9082764d-08fa-4a38-87d1-966da9b11195/image.png)

(출처: [https://velog.io/@hyhy9501/3-1.-스택Stack](https://velog.io/@hyhy9501/3-1.-%EC%8A%A4%ED%83%9DStack))

- 후입선출 (Last In First Out, LIFO) 자료구조

![image.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbcgR9A%2FbtqSX70PCTe%2FdMSMQoJcZhDpq4sRRpu3A0%2Fimg.png)

(출처: https://yoongrammer.tistory.com/45)

- 스택은 **Top** 으로 정해지는 방향으로만 데이터를 삽입하거나 삭제해야함
- 예시
  - 뒤로가기 (웹 브라우저 방문 기록)
  - 실행취소
  - 역순 데이터 구현 함수
- 추상화 함수 (ADT)
  - `push(data)`: 자료 data를 스택에 삽입
  - `pop()`: 자료를 스택에서 꺼냄
  - `peek()`: 마지막 자료를 확인 → 제거 X
  - `is_empty()`: 스택이 비어있는 지 확인
  - `is_full()`: 스택이 가득 차있는지 확인
  - `get_size()`: 스택에 있는 자료 수 확인
- 참고
  - `overflow`: 스택이 완전 꽉 찬 경우
  - `underflow` : 스택이 완전 비어 있는 경우
- 파이썬의 스택
  - 리스트를 사용
  - 스택(리스트) 초기화
    ```python
    stack = []
    ```
  - 자료 삽입 - `push` : 파이썬에서는 `append` 함수로 삽입
    ```python
    stack = [1, 2]
    stack.append(3)
    ```
  - 자료 삭제 - `pop` : 파이썬에서는 똑같이 `pop` 함수로 삭제
    ```python
    top = stack.pop()
    # pop()은 마지막 원소(자료)제거 후 값을 반환
    print(top)
    ```
  - 마지막 자료 가져옴
    ```python
    stack = [1, 2, 3]
    top = stack[-1]
    print(top)
    ```
- 연습 문제

  - 제로 (백준)
    [문제](https://www.acmicpc.net/problem/10773)

# 큐

![image.png](https://velog.velcdn.com/images/hyhy9501/post/606a209d-5184-4850-8751-8d2d5cd7d31e/image.png)

(출처: [https://velog.io/@hyhy9501/3-1.-큐Queue](https://velog.io/@hyhy9501/3-1.-%ED%81%90Queue))

- 선입선출 (First In First Out, FIFO) 자료구조
- 연산
  - `enqueue` : 자료를 큐 뒤에 추가
    - queue의 끝(`rear`/ `back`)에 추가하는 연산
  - `dequeue` : 큐의 맨 앞 자료를 제거하고 반환
    - 큐의 시작(`front` / `head` )에 있는 자료를 제거하고 그 값을 반환
- 파이썬의 큐

  - queue 모듈을 사용
  - queue 초기화

    ```python
    import queue

    q = queue.Queue()
    ```

  - 자료 삽입 - `enqueue` : 파이썬에서는 `put` 으로 사용
    ```python
    q.put(1)
    q.put(2)
    ```
  - 자료 삭제 - `dequeue` : 파이썬에서는 `get` 으로 사용
    ```python
    first = q.get() # 1
    ```
  - 큐 비어있는 지 확인 : `empty()` 로 확인
    ```python
    q.empty()
    ```

- 하지만 성능 차이로 `collections.deque`을 사용하거나 간단한 건 `리스트`로 해결함
  - `pop()`, `append()`, `popleft()`, `pop(0)` 사용
- 연습문제

  - 카드1 (백준)
    [문제](https://www.acmicpc.net/problem/2161)

# 같이 풀 문제

- 같은숫자는싫어
  [문제](https://school.programmers.co.kr/learn/courses/30/lessons/12906)
