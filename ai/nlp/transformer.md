# Transformer

## 1. Transformer의 핵심 컨셉

* 병렬처리
* Self-Attention

### 기존 Seq2Seq 와 다른점

*   RNN/LSTM

    * 단어를 **순서대로(Sequential)** 하나씩 처리

    :arrow\_forward: 문장이 길어지면, 계산이 느려지고, 앞쪽 정보가 뒤까지 가면서 희미해짐
*   Transformer

    * 문장 전체를 **한 번(Parallel)**&#xC5D0; 처리 →

    :arrow\_forward: GPU 연산을 통한 병렬처리가 가능해 속도가 빨라지고, 문장 전체를 처리하니 맨 앞과 맨 뒤의 관계도 즉시 파악
