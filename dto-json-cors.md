# 3. DTO, JSON, CORS

*   F/E는 사용자의 입력을 받아 B/E에 요청하고, B/E는 요청을 처리해 응답

    \-> JSON이라는 포맷을 활용, Java에서는 DTO란 형태로 다룸



*   DTO (Data Transfer Object)

    * 프로세스간의 데이터 교환(IPC)을 위한 객체
    * setter와 getter로만 이뤄짐
    * JavaBeans에서 유래한 Java Bean 또는 그냥 Bean이라고 부르는 형태에 가까움

    \-> Spring Bean, POJO 와는 다름

    * 제대로 된 객체가 아니라 그냥 무기력한 데이터 덩어리
    * C/C++ 에서는 Struct로 구분할 수 있지만, Java에서는 불가능

    \-> 최신 Java에선 record를 활용할 수 있지만, 오래된 Bean 관련 라이브러리에선 지원 X

    * 제약조건(관례, 필수X)
      * 클래스가 직렬화
      * 기본생성자를 포함
      * set, get 혹은 표준 명명법을 따르는 메서드들을 사용해 접근할 수 있어야함
      * 필요한 이벤트 처리 메서드들을 포함
    * DTO는 여러 곳에서 사용될 수 있고, 의미는 계속 확대됨



* Tier간 통신
  * B/E 와 F/E 사이
    * DTO 자체를 그대로 전송할 수 없고, 직렬화(마샬링)을 통해야 함
    * 어떤 직렬화 기술을 사용할 건지 결정해야 함 -> JSON, XML
  * B/E 와 DB 사이
    * 아주 옛날에는 Value Object를 DTO란 의미로 썻지만, Transfer Object라고 정정
    * 한국의 오래된 SI 기업에서는 VO를 DTO란 의미로 사용(DAO와 VO)
    * DDD를 따르는 사람 중 일부는 ORM(JPA, 하이버네이트)는 Active Record + DTO 처럼 접근
  * Data Transfer란 측면에 집중하면 원격이 아닌 경우에도 DTO를 이용



* IPC(Inter-Process Communication)
  * 서로 다른 프로세스, 다른 프로그램이 서로 통신
  * B/E 와 F/E로 나누면 IPC가 필수적
  * 쓸 수 있는 기술
    * File : 가장 기본적인 접근, 원격 환경에서 활용하기 어려움
    * Socket : 파일과 유사하게 읽고 쓸 수 있지만, 원격 환경에서도 활용
      * HTTP 같은 고수준 프로토콜을 활용하면 상대적으로 쉬워짐
      * REST를 활용하면 RPC(SOAP의 일반적인 활용)가 아닌 Resource에 대한 CRUD로 정리
      * Java에서는 RPC를 위해 RMI(Remote Method Invocation)을 제공
        * RPC : 원격 프로시저 호출
        * RMI : 자바 원격 함수 호출
  *   REST에서는 표현을 다뤄야 하고, 이를 위해 데이터를 담는 것 외엔 사실상 아무 것도 하지 않아서 제대로 된 객체라고 볼 수 없는 특별한 객체를 사용

      \-> 무기력한 도메인 모델



* Sefialization
  * 직렬화
  * 객체를 그 자체로 DB에 저장하거나 네트워크로 전송하는건 불가능
  * 객체를 복구할 수 있도록 데이터화
  * 바이너리라면 Byte Stream, text라면 기계가 파싱할 수 있고 사람도 읽을 수 있는 형태를 사용
  * XML, JSON, YAML 같은 형식이 인기
  * 직렬화와 마샬링은 거의 같지만, Java에선 마샬링(Marchalling)을 특수하게 다룸
    * 직렬화 : 역직렬화(Deserialization)를 통해 객체 또는 데이터의 복사본을 만들 수 있음
    * 마샬링 : 직렬화와 같거나, 원격 객체가능. 원격 객체의 경우 메소드 호출은 RPC(또는 RMI)가 됨



*   JSON(JavaScript Object Notation)

    * JavaScript Good Parts로 유명한 Douglas Crockford가 만든 데이터 포맷
    * 사람이 읽기 쉽고, 기계도 해석 또는 생성하기 쉬움
    * JSON.parse, JSON.stringify 로 역직렬화, 직렬화
    * JavaScript의 Object는 기본적으로 key-value 쌍

    \-> Java는 Map이 유사하지만, 스키마 관리 및 타입 안정성을 위해 DTO를 활용

    * 생성 : DTO -> Transfer -> JSON
    * 해석 : JSON -> Transfer -> DTO
    * Java에서 Jackson이란 도구가 유명
    * Spring에서는 Web 의존성을 추가하면 바로 사용



* Jackson ObjectMapper
  * DTO를 JSON으로 변환하거나, JSON을 DTO로 변환
  * JSON의 스키마를 작성한다는 느낌으로
  * 필드보다 getter 메소드 이름을 따른다는 점에 주의
  * 이름을 강제하고 싶으면 @JsonProperty&#x20;
  * Spring DI를 통해 컨트롤러에서 Jackson ObjectMapper를 얻음
  * 스프링이 등록된 객체(Bean)을 관리하고 생성자에 명시하면 받아서 사용가능
  * 사용 = 의존성/의존관계를 주입 받음



* Same-Origin Policy
  * B/E와 F/E가 다른 서버에 있을 때 보안정책을 적용하는 매커니즘
  * 웹 브라우저가 처리하는 보안정책
  * 서버에서는 이미 처리 끝내고 결과를 준 상태에서 얻으려는 리소스의 출처(호스트)가 현재 페이지와 다르면 접근할 수 없게하는 보안 정책
  * 출처에는 포트까지 포함됨
* JSONP
  * script 태그는 동일 출처를 따지지 않는다는 점을 이용, 서버에서 JSON을 직접 전달하는게 아니라, 실행되는 자바스크립트 코드를 전달하는 방식
* CORS (Cross-Origin Resource Sharing)
  * REST API의 응답 헤더에 "Access-Control-Allow-Origin"속성을 포함
  * 서버측에서 브라우저에 F/E에서 요청한 거라면 괜찮다고 알려주는 방식
  * 요청 헤더의 Origin 속성을 참고
* Spring Web MVC에서 CORS
  * ```
    response.setHeader("Access-Control-Allow-Origin", "*");
    ```
  * @CrossOrigin 애너테이션 사용
  *   WebMvcConfigurer

      WebMvcConfigurer 인터페이스에 대한 Spring Bean으로 환경 설정

      ```java
      @Bean
      public WebMvcConfigurer webMvcConfigurer() {
      		return new WebMvcConfigurer() {
      		
      		@Override
      		public void addCorsMappings(CorsRegistry registry) {
      			registry.addMapping("/**")
      			.allowedMethods("GET", "POST", "PATCH", "DELETE", "OPTIONS")
      			.allowedOrigins("<http://localhost:3000>");
      		}
      	};
      }
      ```

      마찬가지로 “\*”을 쓰거나 allowedOrigins 메서드를 따로 써주지 않으면 모든 요청을 허용
