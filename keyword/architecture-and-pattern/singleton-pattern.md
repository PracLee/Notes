# Singleton Pattern

* 생성자가 여러 차례 호줄되더라도 실제로 생성되는 객체는 하나
* 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴



* 장점
  * 메모리 측면 : 고정된 메모리 영역을 사용하여 메모리 누수 방지
  * 데이터 공유 : 전역으로 사용되는 인스턴스이기 때문에 다른 인스턴스들의 접근이 쉬우나, 동시성 문제가 발생할 수 있음&#x20;



* 단점
  * 멀티스레딩 환경에서의 동시성 문제
  * 구현하는 코드 자체가 많이 필요함
  * 인스턴스 자원을 공유하기 때문에 테스트시 매번 인스턴스의 상태를 초기화 해야함
  * 의존 관계상 클라이언트가 구체 클래스에 의존