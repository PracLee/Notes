---
description: 모델이 출력 값을 예측할 때, 입력 데이터의 중요한 부분에 더 주목하게 만드는 기술
---

# Attention Mechanism

## 1.  탄생 배경

* Seq2Seq 모델은 RNN/LSTM 구조를 사용
  * 문장이 아무리 길어도 작은 벡터 하나에 모든 정보를 우겨넣어야 하니, 앞부분의 정보가 사라지는 정보 손실 발생
  * 문장이 길어질수록 학습능력이 떨어지는 기울기 소실 발생

## 2. 핵심 아이디어

* 모든 입력 정보를 다 참고하되, 지금 필요한 정보만 골라보자는 아이디어
*   디코더가 출력을 하나 생성할 때마다, 인코더의 모든 입력 단어들을 다시 훑어봄

    :arrow\_forward: 이때, 모든 단어들을 똑같이 보는게 아니라, **현재 예측해야 할 단어와 관련이 깊은 단어에 더 큰 가중치**를 부여

    :arrow\_forward: 검색 엔진의 작동원리와 유사

## 3. 작동 원리

* 유튜브에서 영상을 찾는 상황. Attention 메커니즘의 3요소(Query, Key, Value)는 다음과 같음
  * Query (Q - 질문): 검색창에 입력한 단어 :arrow\_forward: "파이썬 강의"
  * Key (K - 제목/태그): 유튜브 서버에 저장된 수많은 영상들의 제목들
    * 영상 A 제목: "재미있는 파이썬 강의 기초"
    * 영상 B 제목: "귀여운 뱀(Python) 다큐멘터리"
    * 영상 C 제목: "자바(Java) 프로그래밍 입문"
  * Value (V - 영상 내용): 실제 우리가 보게 될 영상 컨텐츠 자체 (영상 A, B, C의 내용물)

## 4. 작동 과정

1. 유사도 비교 (Dot Product): 검색어(Query: "파이썬 강의")와 영상 제목들(Key)을 하나씩 비교
   * Key A("파이썬 강의")와 비교: 일치도 95% (아주 관련 있음)
   * Key B("뱀 다큐")와 비교: 일치도 10% (단어는 같지만 문맥이 다름)
   * Key C("자바")와 비교: 일치도 5% (관련 없음)
2. 점수화 (Softmax): 일치도를 확률로 변환
   * A: 0.9, B: 0.05, C: 0.05
3. 결과 합성 (Weighted Sum): 확률만큼 영상 내용(Value)을 가져와서 섞음
   * 결과 = (영상 A 내용 \* 0.9) + (영상 B 내용 \* 0.05) + ...

* 검색 엔진 : **"검색어(Q)와 제목(K)을 비교해서, 가장 적절한 컨텐츠(V)를 보여주는 것"**
* Attention : **"현재 상태(Q)와 입력 단어들(K)을 비교해서, 가장 중요한 정보(V)를 가져오는 것"**

## 5. Seq2Seq의 한계 극복

*   가장 큰 문제점: RNN이나 LSTM은 같은 기억을 하나의 hidden state로 계속 압축해 나가므로 **정보 병목(bottleneck)** 발생

    :arrow\_forward: torch 객체를 새로 만듦으로써 확실한 저장소를 구현

    * 기존에 역전파를 하여 loop를 돌아하야는 수고가 없이 바로 인덱스로 접근 가능
    * 마찬가지로 압축하지 않고 다 가지고 있다가, 필요할 때마다 꺼내 봄

## 6. 코드 구현

* Scaled Dot-Product Attention이라는 가장 기본적인 어텐션 수식을 그대로 구현



```python
import torch
import torch.nn.functional as F
import numpy as np

def scaled_dot_product_attention(query, key, value):
    # query 크기: (배치, 1, 차원수) -> 나 지금 뭐 찾고 있어? (예: "apple"의 벡터)
    # key 크기:   (배치, 단어수, 차원수) -> 비교 대상들 (예: 문장 전체 단어들의 벡터)
    # value 크기: (배치, 단어수, 차원수) -> 실제 가져올 내용 (보통 key와 같음)
    
    d_k = query.size(-1) # 차원 수 (스케일링을 위해 필요)

    # 1. 유사도 계산 (MatMul) : Q x K^T
    # transpose(-2, -1)은 행렬의 마지막 두 차원을 뒤집는 것 (전치행렬)
    scores = torch.matmul(query, key.transpose(-2, -1)) / np.sqrt(d_k)
    
    print(f"1. 유사도 점수 (Scores):\n{scores}\n")

    # 2. 확률 변환 (Softmax)
    # dim=-1은 마지막 차원(단어들)에 대해 확률 합이 1이 되게 함
    attention_weights = F.softmax(scores, dim=-1)
    
    print(f"2. 어텐션 가중치 (얼마나 주목할지):\n{attention_weights}\n")

    # 3. 가중합 (Weighted Sum) : Weights x V
    output = torch.matmul(attention_weights, value)
    
    return output, attention_weights

# --- 예시 데이터 생성 ---
# 상황: "I like apple" 이라는 문장이 있고 (Key, Value)
# 현재 디코더가 "좋아해(like)"라는 의미를 찾고 있다고 가정 (Query)

# 단어들을 4차원 벡터로 표현했다고 가정
# Key & Value: [I, like, apple]
K = torch.tensor([[[1.0, 0.0, 1.0, 0.0],   # I
                   [0.0, 10.0, 0.0, 10.0], # like (특징이 아주 뚜렷함)
                   [1.0, 1.0, 1.0, 0.0]]], dtype=torch.float32) # apple
V = K # 보통 K와 V는 같은 값을 씁니다.

# Query: "like"와 비슷한 성질을 찾는 질문
# [0, 5, 0, 5] -> 두번째, 네번째 속성이 강한 녀석을 찾음
Q = torch.tensor([[[0.0, 5.0, 0.0, 5.0]]], dtype=torch.float32)

print(f"Query 벡터: {Q}")
print("-" * 50)

output, weights = scaled_dot_product_attention(Q, K, V)

print(f"3. 최종 결과 벡터 (Context Vector):\n{output}")
```

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

* 행렬 곱셈(유사도 측정) :arrow\_forward: Softmax(확률화) :arrow\_forward: 행렬 곱셈(정보 합성) 과정
