---
description: HTTP
---

# HTTP



1. Client

* Socket은 Closeable이기 때문에 try-with-resources를 써도 된다.

```java
// 중괄호 안에서 열리고 중괄호가 끝나면 닫힘
try (Socket socket = new Socket(host, port)) {
	
}
```



2. Server

* Java에서는 구분을 위해서 ServerSokect이라는 별도의 클래스를 사용, 완전히 구분됨



3. Java Server

* Soket 에서 직접 해야 추출해야 했던 것들을 한번에 처리해줌

```java


// Socket Open
InetSocketAddress address = new InetSocketAddress(8080);
// Server Create
HttpServer httpServer = HttpServer.create(address, 0);

httpServer.createContext("/", (exchange) -> {
    // Get Request Method
    String method = exchange.getRequestMethod();
    System.out.println("method : " + method);
    
    // Get URI
    URI uri = exchange.getRequestURI();
    String path = uri.getPath();
    System.out.println("path : " + path);
    
    // Get Headers && Values
    Headers headers = exchange.getRequestHeaders();
    for (String key : headers.keySet()){
        System.out.println("key : " + key);
        List<String> values = headers.get(key);

        for(String value : values){
            System.out.println("value : " + value);
        }
    }
    
    // Get Request Body
    InputStream inputStream = exchange.getRequestBody();
    byte[] bytes = inputStream.readAllBytes();
    String body = new String(bytes);
    System.out.println("body : " + body);

    // Set Response Header && Body
    byte[] resByte = resBody.getBytes();
    exchange.sendResponseHeaders(200, resByte.length);
    OutputStream outputStream = exchange.getResponseBody();
    outputStream.write(resByte);
    outputStream.flush();
});

// Server Start
httpServer.start();

```



4. Spring Server

* Tomcat 을 이용해&#x20;
