# Back-end VS Front-end

* System을 여러 Tier/Layer로 구분
* Tier는 물리적인 구분
* Layer는 논리적인 구분
* 사용자와 가까운 부분을 F/E, 사용자에게서 먼 부분을 B/E
* 최근에는 HTTP, 정확히는 Web기술을 활용하고,  REST API를 사용
  * 이 외에도 SOAP, GraphQL 등 다른 것도 사용
* 간략하게 말하면 Server == B/E, Client == F/E
* JS를 개발할때 F/E
* Tomcat등의 WAS위에 작동하는 Java Servlet, Spring Boot 를 개발할때 B/E
