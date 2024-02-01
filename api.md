# API

* Application Programming Interface
* 컴퓨터나 프로그램 사이의 연결
* Interface
  * 소통 (Communication)
  * 명세 (Specification)
  * 정보은닉 (Information Hiding - Principle)
  * 캡슐화 (Encapsulation - Technique)
  * 실행 (Implementation)



REST(Representational State Transfer)

* API 를 사용하기 위한 원칙
* Roy Fielding - “[Architectural Styles and the Design of Network-based Software Architectures](https://www.ics.uci.edu/\~fielding/pubs/dissertation/top.htm)” (2000)의 방식을 채택
*   제약조건

    * Starting with the Null Style
    * Client-Server
    * Client-Server
    * Cache
    * Uniform Interface → 핵심!
      * 컴포넌트(서버-클라이언트)간의 Uniform Interface
      * 구현 분리
      * 규칙적인 Standardized form을 쓰기 때문에 비효율적일 수 있음
      * 대규모의 Hypermedia data를 전송하는데 효과적
    * 필딩 제약 조건 : 따르냐 안따르냐를 따라 RESTFUL?
      * URI등으로 리소스를 식별
      * 표현으로 리소스를 조작
      * **메시지는 자기 서술적이기 때문에 처리/변환 가능**
        * JSON같은 범용 포맷을 작게 사용하면 해석할수 없으므로 MIME 타입으로 설명
        * application/json -> application/dns+json
      * **Hypermedia as the Engine of Application State -> HATEOAS**


* API를 위한 아키텍처 스타일이 아님 -> web에서의 일반적이 전송을 위한 아키텍처 스타일
* 아키텍처 요소에서 리소스와 표현을 구분
  * Resourcd -> 추상
  * Representation -> Data + Metadata + Meta-metadata...
    * 사실상 HTTP 메시지
    * 어떻게 조작할 것인가 HTTP Method로 표현
    * 무엇으로 조작할 것인가 Content-Type, Body로 표현
* 리소스는 File 그 자체가 아님 : 리소스, 표현, 실제 데이터는 구분됨
* 로이 필딩은 필딩 제약 조건을 지키지 않는 API를 REST API라고 부르는것에 반대
* 업계에서는 그냥 리처드슨의 성숙도 모델 레벨 2만 만족해도 REST API라고 부름



* URI(Uniform Resource Identifier) : 리소스를 식별하는 방법
  * 식별할때는 식별자(Identifier == id)를 활용
  * URL(Uniform Resource Locator) : 리소스의 위치
  * URN(Uniform Resource Name) : 리소스의 유니크한 위치
* URI는 대부분 URL -> 크게 구분하지 않고 주로 URL로 통일해서 사용



* MINE Type (Content Type)
* \<type>/\<subtype>의 형태
* HTTP Headers에 Content-Type 속성으로 전달
* [IANA](https://www.iana.org/assignments/media-types/media-types.xhtml)에 등록된 목록을 참고



* Collection Pattern
* 여러 리소스를 하나의 그룹으로 묶는 것
* Collection Pattern을 쓰지 않는 경우:
  * /test-post
* Collection Pattern을 쓰는 경우:
  * /posts ⇒ 모든 게시물을 하나의 URI로 표현(게시물 목록으로도 활용 가능). 일반적으로 복수형을 사용
  * `/posts/the-first`
  * `/posts/test`
  * `/posts/{id}` 또는 `/posts/:id` 등으로 일반적인 형태로 쓸 수 있다. 여기서 {id}를 {post\_id}나 {postId} 등으로 표기할 수도 있다. 여기서는 그냥 Post ID라고 부를 예정.
* Post ID는 리소스의 ID가 아님에 주의!
* Resource ID = URI = URL
* Post ID = Resource ID를 구성하는 요소 중 하나. posts 그룹 내 식별자(ID).





