# Binary Search

## 이진탐색

* 정렬된 연속형데이터에서 원하는 값을 효율적으로 찾는 탐색알고리즘
* 시간복잡도 O(log n)

### 예시

* 가나다 순으로 정렬된 사전에서 특정 문자를 찾을때
  1. 처음에 절반을 나누고 나온페이지에서 나온 이름을 보고 뒤에 있는지 앞에 있는지 확인
  2. 뒤에있다면 앞페이지들을 버리고, 앞에 있다면 뒤페이지를 버리고 1번부터 다시 시작

```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1  # 못 찾은 경우
```

### 장점

* 탐색속도가 매우 빠르다
* 계산 논리가 단순하고 구현이 쉽다
* 메모리를 추가로 거의 쓰지 않는다

### 단점

* 반드시 정렬된 데이터이여야함
* 인덱스로 바로 접근 가능한 구조가 필요
* 삽입/삭제가 자주 일어나면 비효율적(정렬상태 유지비용)
* 중복값 처리나 범위 탐색은 추가 로직 필요 (같은 값이 여러 개일 때 “첫 번째 위치” or “마지막 위치”)
