# Java try-with-resources

* Java 7에서 도입
* 명시적인 리소스 해제가 필요한 경우 사용
* AutoCloseable 인터페이스를 구현한 객체들을 자동으로 닫아줌

```java
try (OutputStream output = new FileOutputStream("example.txt")) {
    // code 작성
}
catch (IOException e){
    e.printStackTrace();
}
```
