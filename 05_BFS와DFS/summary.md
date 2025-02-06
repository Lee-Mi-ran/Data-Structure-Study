> # 그래프 탐색
![그래프예시](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcGWUf5%2FbtsBDP3rZA3%2FO7fKCvWnuf3nztOduREzgk%2Fimg.png)<br>
(출처: https://codingsmu.tistory.com/170)
: 그래프를 탐색하는 것은 각 노드를 방문하는 것을 의미

- 그래프는 노드의 집합과 간선의 집합으로 구성됨 `G = (V, E)`
    - <i>V</i> : 노드의 집합
    - <i>E</i> : 노드 간 연결되는 간선 집합
    ![그래프](https://wikidocs.net/images/page/196182/ds-088.png)<br>
        ```
        V = {1, 2, 3, 4, 5}
        E = {(1, 2), (1, 3),(1, 5), (2, 3), (3, 4), (3, 5), (4, 5)}
        ```

> # 그래프 종류
- 무방향 그래프: 두 노드 간 방향이 없음
- 방향 그래프: 두 노드간 방향이 있음
- 가중 그래프: 간선마다 가중치를 부여(비용, 시간 등 고려)해서 방향/무방향으로 연결된 그래프

> # 그래프 구현
![그래프](https://wikidocs.net/images/page/196182/ds-090.png)<br>
```python
# 무방향 그래프
Graph1 = {
    1: [2, 3, 5],
    2: [1, 3],
    3: [1, 2, 4],
    4: [3, 5],
    5: [1, 4]
}

# 방향 그래프
Graph2 = {
    1: [2, 3],
    2: [3],
    3: [4],
    4: [],
    5: [1, 4]
}
```
- 대부분 그래프 구현은 딕셔너리 형태로 구현됨

> # 파이썬 구현
- BFS 구현: 큐로 구현
    - 최단 경로 구하는 문제에 용이
    ```python
    from collections import deque

    # BFS 함수 정의
    def bfs(start, N, G):
        # 방문 여부를 추적하는 리스트, 시작점은 방문처리 하지 않음
        visited = [False] * (N + 1)
        
        # 큐를 생성, 시작 노드를 큐에 넣음
        que = deque()
        que.append(start)
        
        # 큐가 빌 때까지 반복
        while que:
            v = que.popleft()  # 큐에서 하나씩 꺼내기
            
            # 아직 방문하지 않았다면
            if not visited[v]:
                visited[v] = True  # 방문 처리
                
                # 현재 노드와 연결된 다른 노드를 큐에 넣기
                for u in G[v]:
                    if not visited[u]:  # 이미 방문한 노드는 큐에 넣지 않음
                        que.append(u)
        
        # BFS가 끝나면 모든 노드의 방문 여부를 반환
        return visited

    # 예시: 그래프 정의
    N = 6  # 노드 수
    G = {
        1: [2, 3],
        2: [1, 4, 5],
        3: [1, 6],
        4: [2],
        5: [2],
        6: [3]
    }

    # BFS 호출
    start_node = 1  # 시작 노드
    visited_nodes = bfs(start_node, N, G)

    # 방문한 노드 출력
    print("방문한 노드:", visited_nodes)

    # 방문한 노드를 보기 쉽게 출력 (True인 노드들만 출력)
    print("방문된 노드 (True인 값):")
    for i in range(1, N+1):
        if visited_nodes[i]:  # 방문한 노드만 출력
            print(i, end=' ')

    ```
    
    start == 1 <br>
    방문한 노드: [False, True, True, True, True, True, True]<br>
    방문된 노드 (True인 값): 1 2 3 4 5 6 

- DFS 구현: 재귀 또는 스택으로 구현
    - 백트래킹에 용이
    - 재귀
    ```python
    # DFS 함수 정의
    def dfs(start, N, G, visited=None):
        # visited 리스트가 주어지지 않으면 기본적으로 False로 초기화 (시작 시 방문하지 않은 상태로 설정)
        if visited is None:
            visited = [False] * (N + 1)
        
        # 현재 노드 방문 처리
        visited[start] = True
        
        # 현재 노드에서 연결된 모든 노드들에 대해 재귀적으로 DFS 수행
        for v in G[start]:
            # 연결된 노드 중 아직 방문하지 않은 노드가 있으면 그 노드를 시작점으로 DFS 호출
            if not visited[v]:
                dfs(v, N, G, visited) 
        
        # DFS가 끝난 후 모든 노드의 방문 여부를 반환
        return visited

    # 예시: 그래프 정의
    N = 6  # 노드 수
    G = {
        1: [2, 3],
        2: [1, 4, 5],
        3: [1, 6],
        4: [2],
        5: [2],
        6: [3]
    }

    # DFS 호출
    start_node = 1  # 시작 노드
    visited_nodes = dfs(start_node, N, G)

    # 방문한 노드 출력
    print("방문한 노드:", visited_nodes)

    # 방문된 노드를 보기 쉽게 출력 (True인 노드들만 출력)
    print("방문된 노드 (True인 값):")
    for i in range(1, N+1):
        if visited_nodes[i]:  # 방문한 노드만 출력
            print(i, end=' ')

    ```

    start == 1 <br>
    방문한 노드: [False, True, True, True, True, True, True]<br>
    방문된 노드 (True인 값): 1 2 3 4 5 6 

    - 스택 (반복문)
    ```python
    from collections import deque

    # DFS 함수 정의 (반복문 방식)
    def dfs(start, N, G):
        # 방문 여부를 추적하는 리스트, 시작점은 방문하지 않은 상태로 설정
        visited = [False] * (N + 1)
        
        # 스택을 생성하고, 시작 노드를 스택에 넣음
        stack = deque()
        stack.append(start)
        
        # 스택이 빌 때까지 반복
        while stack:
            v = stack.pop()  # 스택에서 가장 위에 있는 노드 꺼내기 (LIFO 방식)
            
            # 아직 방문하지 않았다면
            if not visited[v]:
                visited[v] = True  # 방문 처리
                
                # 현재 노드와 연결된 모든 노드를 스택에 넣기
                for u in G[v]:
                    if not visited[u]:  # 이미 방문한 노드는 스택에 넣지 않음
                        stack.append(u)
        
        # DFS가 끝나면 모든 노드의 방문 여부를 반환
        return visited

    # 예시: 그래프 정의
    N = 6  # 노드 수
    G = {
        1: [2, 3],
        2: [1, 4, 5],
        3: [1, 6],
        4: [2],
        5: [2],
        6: [3]
    }

    # DFS 호출
    start_node = 1  # 시작 노드
    visited_nodes = dfs(start_node, N, G)

    # 방문한 노드 출력
    print("방문한 노드:", visited_nodes)

    # 방문된 노드를 보기 쉽게 출력 (True인 노드들만 출력)
    print("방문된 노드 (True인 값):")
    for i in range(1, N+1):
        if visited_nodes[i]:  # 방문한 노드만 출력
            print(i, end=' ')

    ```
    위와 동일

- 연습문제
    - 타겟넘버 (https://school.programmers.co.kr/learn/courses/30/lessons/43165)
    - 게임 맵 최단거리 (https://school.programmers.co.kr/learn/courses/30/lessons/1844)