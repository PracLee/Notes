# Sort

### 1. 선택정렬

(![선택정렬](https://www.programiz.com/sites/tutorial2program/files/Selection-sort-0.png))

* 가장 작은 요소를 선택해서 앞으로 보내는 정렬
* 항상 전체 탑색 -> 최소값 찾기 -> 교환 의 패턴으로 진행
* 시간복잡도는 O(n²)로 고정 -> 매번 최소값을 찾기 위해 전체탐색이 필요함(n \* n)
* 구현이 아주 쉽다.
* 교환 횟수는 적지만 비교 연산이 매우 많음.
* 같은 값의 순서가 바뀔 수 있음

```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i     # 깨알같은 Greedy
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr
```



### 2. 삽입정렬

(![삽입정렬](https://media.geeksforgeeks.org/wp-content/uploads/20240802210251/Insertion-sorting.png))

* 앞쪽은 이미 정렬된 상태라고 생각하고, 새 값이 들어올때 적절한 위치에 끼워 넣기
* 시간복잡도 최악일때 O(n²), 최선 O(n)
* 거의 정렬된 데이터일 때 매우 빠름
* 비교적 안정적이고 구현도 쉬움

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = key
    return arr
```

### 3. 버블 정렬

![버블 정렬](https://www.productplan.com/uploads/bubble-sort-1024x683-2.png)

* 두 항목을 비교해서 더 큰값을 뒤로 보내는 정렬
* 시간복잡도 최악일때 O(n²), 최선 O(n)

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```

### 4. 퀵정렬

![퀵정렬](https://media.geeksforgeeks.org/wp-content/uploads/20240926172924/Heap-Sort-Recursive-Illustration.webp)

* 중심축을 하나 정해서 작은값들은 왼쪽, 큰 값들은 오른쪽으로 분할
* 시간복잡도 최선 O(n log n), 최악 O(n²)(이미 정렬된 배열에서 첫 요소를 피벗으로 잡는 경우)
* 분할된 양쪽을 재귀로 계속 정렬
* 평균적으로 가장 빠른 정렬중 하나

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    mid  = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + mid + quick_sort(right)
```

### 5. 힙정렬

(![힙정렬](https://he-s3.s3.amazonaws.com/media/uploads/e9d6f12.png))

* Heap이라는 완전이진트리 기반 우선순위 큐 사용
* 시간복잡도: O(n log n) (힙 삽입/삭제가 log n이기 때문에 일정)
* 루트를 하나씩 꺼내 배열 뒤에서부터 채워나감

```python
import heapq
def heap_sort(arr):
    h = []
    for v in arr:
        heapq.heappush(h, v)
    return [heapq.heappop(h) for _ in range(len(h))]
```

### 6. 병합정렬

(![병합정렬](https://www.w3schools.com/dsa/img_mergesort_long.png))

* 배열을 나눌 수 없을정도로 반으로 쪼개고, 쪼갠걸 정렬하면서 병합
* 시간복잡도 항상 O(n log n)
* 추가적인 메모리 공간이 필요함

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    result = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    result.extend(left[i:])
    result.extend(right[j:])
    return result
```
