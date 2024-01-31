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
  * Level 0 : HTTP 사용
    * 웹 메커니즘을 사용하지 않고 HTTP를 원격 통신을 위한 전송 시스템으로 사용
    * 하나의 endpoint를 사용, 하나의 endpoint에서 여러 동작, 매개변수 전달 method는 POST사용
  * Level 1 : 개별 리소스 개념
    * 모든 요청을 단일 endpoint로 보내는 것이 아니라 개별 리소스와 통신, 리소스별로 고유한 URI 사용
    * HTTP method는 GET과 POST만 사용,  Error인 경우에도 Status Code 200으로 전달, HTTP headers에 Content-Type, Cache 관련정보 제공 X
  * Level 2 : HTTP method 원칙 준수
    * HTTP method인 GET, POST, PUT, DELETE를 사용해 CRUD를 나타내고 메시지에 Status Code도 담겨 반환
    * URI에는 행위(Action)가 포함되지 않고 HTTP Method로 표현
    * GET은 매번 같은 결과를 반환하고, 헤더에 Content-Type을 제공하며 멱등성을 보장하는 GET의 경우 캐시가 적용
  * Level 3 : HATEOAS 원칙 준수
    * 응답에 다음 가능한 행동을 명시





