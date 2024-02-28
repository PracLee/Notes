# Stateless VS Stateful

1. Stateless

* UDP와 HTTP통신 기본
* Client - Server 관계에서 Server가 Client와의 통신 Socket을 닫음
* Server의 확장성이 높기 때문에 대처를 수월하게 할 수 있음
* Client의 요청에 상대적으로 많은 데이터가 소모됨
* stateless의 단점을 보완하기 위해 아래와 같은 방법을 사용
  * 브라우져의 Cookie나 Server의 Session 메모리에 저장
  * Client의 요청 헤더에 Token을 추가함으로 인증 요소를 덜 수 있음



2. Stateful

* TCP와 3-way handshaking
* Server가 Client와의 통신 Socket을 열어 놓은상태로 유지
* Server의 문제로 다른서버로 대체 되었을때 문제 발생
