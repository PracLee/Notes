# HTTP message Sturucture

1. HTTP Request, Response

* Start Line : method, target, version으로 구성

```
GET /test.html HTTP/1.1
[methot] [target] [version]
```

* Headers : request에 대한 추가 정보 key : value 로 구성

```
Host : google.com
Accept : text/html
...
```

* Body :  전송하는 데이터를 담는 부분, 없다면 empty

```
{
    "key": "value"
    ...
}
```

2. HTTP methods : 수행해야 할 동작을 지정

* GET : 조회
* POST : 데이터 처리, 주로 등록
* PUT : 덮어쓰기, 없으면 생성
* PATCH : 리소스 부분 변경
* DELETE : 삭제
* HEAD : GET과 동일하지만 body를 제외하고 상태와 header만 반환
* OPTIONS : 대상 리소스에 통신 가능한 옵션을 설명
* CONNECT : 대상 자원으로 식별되는 서버에 대한 터널 설정
* TRACE : 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트 수행



3. HTTP response status code

* 100 \~ : 정보응답
* 200 \~ : 성공
* 300 \~ : 리다이렉션
* 400 \~ : Client 오류
* 500 \~ : Server 오류
