# Java ServerSocket

* Java에서 Socket 통신을 위한 Class
* 연결, 데이터 I/O 의 기본적인 기능 제공
* Network Programming에 주로 사용



1.  **ServerSocket 생성**

    ```java
    javaCopy codeint portNumber = 12345; // 예시 포트 번호
    ServerSocket serverSocket = new ServerSocket(portNumber);
    ```
2.  **연결 대기 :** 클라이언트의 연결 요청 대기, `accept()` 메서드를 호출하면 클라이언트가 연결될 때까지 대기

    ```java
    javaCopy codeSocket clientSocket = serverSocket.accept();
    ```
3.  **데이터 송수신:** `Socket` 클래스를 사용하여 클라이언트와의 데이터 송수신을 수행

    ```java
    javaCopy codeInputStream inputStream = clientSocket.getInputStream();
    OutputStream outputStream = clientSocket.getOutputStream();
    ```
4.  **연결 종료:** 통신이 끝나면 소켓을 닫아 리소스를 해제

    ```java
    javaCopy codeclientSocket.close();
    serverSocket.close();
    ```

* ServerSocket은 예외를 던질 수 있으므로 예외 처리가 필요&#x20;
* IOException 이 발생할 수 있음

\
