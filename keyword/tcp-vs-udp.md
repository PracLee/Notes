# TCP VS UDP

1. TCP (Transmission Control Protocol)

* 연결 지향 방식으로 패킷 교환 방식을 사용
* 흐름 및 혼잡 제어
* UDP에 비해 상대적으로 속도가 느림
* 3-way handshake를 통해 통신 시작
  * Client가 Server에게 SYN을 날려 통신 가능 유무 확인
  * Server가 Client에게 SYN/ACK를 날려 통신 준비 완료 알림
  * Client가 Server에게 ACK를 날려 전송 시작 알림
* 4-way handshake를 통해 통신 종료
  * Client가 Server에게 FIN flag를 날려 연결을 종료하겠다고 알림, Client FIN-WAIT 상태
  * Server가 Client에게 ACK를 날려 확인 메시지 보냄, Server CLOSE-WAIT 상태
  * Server가 Client에게 FIN flag를 날려 연결해지 준비완료 상태 알림, Server LAST-ACK 상태
  * Client가 Server에게 해지준비가 되었다는 ACK 보냄, Client TIME-WAIT 상태 (일정시간 후 CLOSE)



2. UDP (User Datagram Protocol)

* 비연결형 서비스로 데이터그램 방식을 제공
* 정보를 주고 받을 때 신호절차 X
* UDP Header의 CheckSum 필드를 통해 최소한의 오류 검출
* 신뢰성이 낮지만 속도가 빠름
* 연결 자체가 없어, Socket의 구분이 없음
* IP기반 데이터 전송
* 1:1, 1:N, N:N으로 연결 될 수 있음
* 데이터그램(message) 단위로 전송됨 (최대크기 65535 byte, 초과하면 잘라서 보냄)
* 흐름제어가 없어 데이터 무결성확인 불가
* 성능 위주의 서비스에서 사용
