# 2. REST (Representational State Transfer)



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



*   Collection Pattern

    * 여러 리소스를 하나의 그룹으로 묶는 것
    * Collection Pattern을 쓰지 않는 경우:
      * /test-post
    * Collection Pattern을 쓰는 경우:
      * /posts ⇒ 모든 게시물을 하나의 URI로 표현(게시물 목록으로도 활용 가능). 일반적으로 복수형을 사용
        * `/posts/the-first`
        * `/posts/test`
        * `/posts/{id}` 또는 `/posts/:id` 등으로 일반적인 형태로 쓸 수 있다. 여기서 {id}를 {post\_id}나 {postId} 등으로 표기할 수도 있다. 여기서는 그냥 Post ID라고 부를 예정.
        * Post ID는 리소스의 ID가 아님 -> Resource ID = URI = URL
        * 그룹명은 복수형으로 사용하기 때문에 Item을 지정할때도 일반적으로 복수형으로 쓰임
    * Post ID = Resource ID를 구성하는 요소 중 하나. posts 그룹 내 식별자(ID).
    * 특정 게시물에 댓글이 달리는 상황이라면 디렉터리처럼 구성할 수 있음

    \-> /posts/{post\_id}/comments => Collection

    * 특정 게시물을 고치는 페이지를 표현하고 싶다면 -> /posts/{id}/edit
    * REST API 의 경우 페이지만 표현할 일은 거의 없음 -> 표현은 F/E -> B/E 는 URL만 쓰도록 제약해도 무방
    * 그룹이 아닌경우 단수형을 써도 됨

    \-> /session

    \-> /edit?...



* CQS
  * CRUD를 중요한 특징에 따라 구분
  * Command와 Query로 나뉨
    * Command -> Create, Update, Delete -> 상태가 변함, 안전하지 않음
    * Query -> Read -> 상태가 변하지 않음, 안전함, 분산, 캐시 등이 수월함
  * Collection Pattern과 HTTP Method를 이용해 CRUD를 표현
    * GET -> Read
    * POST -> Create
    * PUT, PATCH -> Update
    *   DELETE -> Delete

        * GET /posts -> 게시물 목록 Read Collection
        * GET /posts/{id} -> 게시물 상세 Read Element
        * POST /posts -> 게시물 생성 Create
        * PUT(전체), PATCH(일부) /posts/{id} -> 게시물 수정 Update Element
        * DELETE /posts/{id} -> 게시물 삭제 Delement

        \-> 종종 Bulk update, Bulk delete 등을 함. 이럴때는 Collection 활용 후 API 스펙 문서에 명시
    * 로그인/로그아웃은 추상적인 개념인 session 사용
      * POST /session -> 세션 생성, 로그인
      * DELETE /session -> 세션 파괴, 로그아웃
      * GET /session -> 세션 확인, 내 정보 확인?
      * GET /users/me -> User ID를 me라고 쓰면, 현재 사용자의 User ID로 처리하게 정하고 API 스펙 문서에 명시

