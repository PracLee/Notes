# isqrt(int)

```python
import math


def solution(n):
    root = math.isqrt(n) ## 제곱근을 구하는 함수
    
    if root * root == n:
        return (root + 1) ** 2
    else:
        return -1
```
