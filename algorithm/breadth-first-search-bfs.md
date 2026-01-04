---
description: 너비 우선 탐색
---

# Breadth-First Search(BFS)

<figure><img src="https://www3.cs.stonybrook.edu/~skiena/combinatorica/animations/anim/bfs.gif" alt=""><figcaption></figcaption></figure>

## 너비 우선 탐색(BFS)

* 시작 정점에서 가까운 정점부터 차례대로 방문하는 알고리즘 -> 넓게 먼저 퍼져나가는 방식

### 작동 방식

1. 시작점 방문
2. 인접 노드 방문
3. 다음 깊이 방문
4. 1\~3 반복

* 선착순 구조(FIFO)라서 Queue 가 가장 중요
  * Stack(LIFO)를 사용시 깊이 우선 탐색(DFS)가 되어버림
  * 순서를 강제 하기 위해서 Queue 사용

### 사용 시기

* 최단 거리를 찾을때 가장 강력(두 지점 사이의 최단 경로 찾기, SNS 친구 추천, 크롤링 중 링크된 페이지들을 층별로 수집할 때)



### Python 코드 예시

```python
from collections import deque

# 1. 그래프 정의 (인접 리스트 방식)
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

def bfs(graph, start_node):
    visited = [] # 방문한 노드를 기록할 리스트
    queue = deque([start_node]) # 큐 생성 및 시작 노드 삽입
    
    # 큐가 빌 때까지 반복 (더 이상 갈 곳이 없을 때까지)
    while queue:
        # 1. 큐에서 노드 하나를 꺼냄 (가장 먼저 들어온 것)
        current_node = queue.popleft()
        
        # 2. 방문하지 않은 노드라면 처리
        if current_node not in visited:
            visited.append(current_node)
            print(f"{current_node} 방문!")
            
            # 3. 인접한 노드들을 큐에 추가
            # (이미 방문한 노드는 큐에 넣지 않도록 필터링하면 더 효율적)
            for neighbor in graph[current_node]:
                if neighbor not in visited:
                    queue.append(neighbor)
                    
    return visited

# 실행
print("BFS 탐색 순서:")
bfs(graph, 'A')
```

실행 결과 (순서): `A -> B -> C -> D -> E -> F` (A에서 시작해 가까운 B, C를 먼저 가고, 그 다음 깊이인 D, E, F를 방문)