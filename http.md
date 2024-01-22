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
