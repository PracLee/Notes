# Port

* 특정 네트워크 연결을 통해 통신할 수 있돌고 식별되는 논리적인 엔터티
* 0 \~ 65535까지의 숫자로 식별됨
* TCP || UDP Protocol 에서 사용
* 특정 Protocol 을 사용하는 App이나 Service를 식별
* 하나의 IP Adress에서 여러 Process가 통신할 수 있도록 Multiplexing 지원
* 동일한 Port 를 여러 Process 에서 동시에 사용하면 충돌이 발생



Port와 Socket의 관계는 은행과 창구의 관계로 볼수 있을듯 하다.

Port가 특정은행, Socket은 처리해야하는 창구
