# Transformer

## 1. Transformer의 핵심 컨셉

* 병렬처리
* Self-Attention

### 기존 Seq2Seq 와 다른점

*   RNN/LSTM

    * 단어를 **순서대로(Sequential)** 하나씩 처리

    :arrow\_forward: 문장이 길어지면, 계산이 느려지고, 앞쪽 정보가 뒤까지 가면서 희미해짐
*   Transformer

    * 문장 전체를 **한 번(Parallel)**&#xC5D0; 처리 → Self-Attention 사용

    :arrow\_forward: GPU 연산을 통한 병렬처리가 가능해 속도가 빨라지고, 문장 전체를 처리하니 맨 앞과 맨 뒤의 관계도 즉시 파악

## 2. Transformer 구조

* Encoder/Decoder로 구분

:arrow\_forward: 진화모델 BERT, GPT는 각각 Encoder, Decoder 사용



### Transformer의 핵심 구조

#### 1. Positional Encoding (위치 인코딩)

* Transformer는 한 번에 처리하기 때문에 토큰 자체에 순서 정보가 없음

:arrow\_right: 각 토큰 임베딩에 위치정보를 더해서, 모델이 순서/거리를 학습할 수 있게 함\\



#### 2. (Multi-Head) Self-Attention

Transformer의 핵심은 **Attention**, 특히 Encoder에서는 **Self-Attention**

* **Self-Attention이란?**
  * 각 토큰이 문장 안의 토큰을 참고 하고서 **지금 토큰을 이해하는 데 중요한 토큰에 더 큰 비중(가중치)**&#xC744; 주어 정보를 섞는 과정
    * 예: “The animal didn’t cross the street because it was too tired.”
      * “it”이 animal을 가리키는지 street를 가리키는지 판단하는 상황
        * 주변 단어들과 어떤 관계를 가지는지(‘too tired’는 생물에 더 어울림)를 보고,
        * “it”이 참고해야 할 대상(동물)에 더 높은 가중치를 줌
*   **Multi-Head**?

    * Self-Attention을 한 번만 하면 "관계"를 한 종류의 관점으로만 봄

    :arrow\_right: 여러 개의 Head로 나누어 서로 다른 관점의 관계를 동시에 학습

    * Attention의 역할 분담
      * 주어-동사 같은 문법 관계, 동음이의어 구분 같은 의미 관계, **장거리 의존(앞-뒤 연결)** 등

> Encoder의 Self-Attention은 양방향(문장 전체를 자유롭게 참고)
>
> Decoder의 Self-Attention은 Masked(미래 토큰을 못 보게 막음)

#### 3. Feed Forward Network(FFN) + Residual(Add) + LayerNorm(Norm)

Attention은 "무엇을 참고할지"를 결정해 정보를 섞는 단계

섞어놓기만 하면 표현력이 부족함 :arrow\_right: 결과를 **비선형 변환(신경망)**&#xC73C;로 가공 :arrow\_forward: FFN

*   FFN: 각 토큰 벡터에 동일한 작은 MLP를 적용해 표현을 강화

    **정보를 어디서 가져올지(관계/참고)**
*   Residual(Add): 입력을 출력에 더해 정보가 사라지지 않게 하고, 학습을 안정

    (깊은 네트워크에서 성능/학습 안정성에 매우 중요)

    **가져온 정보를 어떻게 가공할지(표현력 증가)**
*   LayerNorm(Norm): 값의 분포를 정리해서 학습을 더 안정적으로 만듦

    **깊게 쌓아도 학습이 무너지지 않게 안전장치**
