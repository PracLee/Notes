# REST (Representational State Transfer)

* Roy Fielding - “[Architectural Styles and the Design of Network-based Software Architectures](https://www.ics.uci.edu/\~fielding/pubs/dissertation/top.htm)” (2000) 에서 제안한 기기간의 통신 모델



* **제약조건**
  * Starting with the Null Style
  * Client-Server
  * Stateless
  * Cache
  * **Uniform Interface**
  * Layered System
  * Code-On-Demand



*   **Uniform Interface**

    * 구성요소간의 동일한 Interface를 강조
    * S/W 공학의 일반원리 -> 컴포넌트(기기-기기, 기기-프로그램)에 적용

    \->  시스템 아키텍처를 단순화, 가시성 향상

    * 제공하는 서비스와 구현을 분리시켜 발전 가능성 향상
    * 통일된 인터페이스가 비효율성이 발생할 수 있음
    * 대규모 하이퍼미디어 데이터 전송에 효율적으로 설계됨

    \-> 결과적으로 다른 형태의 아키텍처 상호 작용에는 최적이 아닌 인터페이스



* Rechardoson의 REST API 성숙도 모델
* 총 4단계로 나누어 져서 단계의 조건에 만족할 수록 REST에 가까워짐
  * Level 0 : 리소스 구분 없이 설계된 HTTP API
  * Level 1 : HTTP&#x20;





