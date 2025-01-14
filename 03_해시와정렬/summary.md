> # 해시
- 데이터를 고정된 크기의 값으로 변환
- 해시함수: 해시 기능을 구현한 함수
- 해시테이블: 빠른 검색을 위해 해시값을 이용해 데이터를 저장하는 자료구조

# 파이썬의 해시 함수
- 파이썬의 내장 함수 hash()를 통해 객체에 대한 고유한 정수값을 반환
    ```python
    name = 'mirae'
    hash_value = hash(name) # 5440103584708522307
    ```

# 파이썬의 해시 테이블
- 파이썬의 딕셔너리는 해시테이블을 기반으로 구현됨 
    ```python
    # 딕셔너리생성
    hash_table = {} 

    # key, value 추가
    hash_table["apple"] = 1

    # 값 조회: key
    hash_table["apple"] #  1

    # 키 존재 확인
    "apple" in hash_table # True

    # 키 삭제
    del hash_table["apple"]
    ```

# 연습문제
- https://school.programmers.co.kr/learn/courses/30/lessons/42576 (완주하지 못한 선수)

<br/>

> # 정렬
- 데이터를 특정 기준에 따라 순서대로 나열하는 과정

# 파이썬의 정렬
- 기본적으로 문자형은 사전순, 정수형은 크기순으로 정렬
    ```python
    # 1. .sort(): 오름차순 정렬, 기존 변경
    # 내림차순 원할 경우 reverse=True 입력
    li1 = [3, 2, 1, 4]
    li2 = [3, 2, 1, 4]
    li1.sort() # [1, 2, 3, 4]
    li2.sort(reverse=True)  # [4, 3, 2, 1]

    # 2. sorted(): 오름차순 정렬, 반환 있음
    li1 = [3, 2, 1, 4]
    li2 = sorted(li1) # [1, 2, 3, 4]

    # 참고: 코딩테스트에 많이 사용
    # 문자열 길이순 내림차순: key 속성
    li1 = ["aa", "bbb", "c", "dddd"]
    li2 = sorted(li1, key=len, reverse=True) # # ['dddd', 'bbb', 'aa', 'c']

    # 참고: 코딩테스트에 많이 사용
    # 딕셔너리 정렬
    info = [
        {'name': 'Kang1', 'age': 20 }, 
        {'name': 'Kang2','age': 33}
        ]

    sorted_info = sorted(dic, key=lambda i:i['name'], reverse=True) # [{'name': 'Kang2','age': 33}, {'name': 'Kang1', 'age': 20}] 
    ```
# 연습문제
- https://school.programmers.co.kr/learn/courses/30/lessons/42748 (k번째수)

# 같이 풀 문제
- https://school.programmers.co.kr/learn/courses/30/lessons/1845 (폰켓몬)