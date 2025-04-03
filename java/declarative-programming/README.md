# Declarative Programming

1. 명령형 프로그래밍

```java
List<String> list = Arrays.asList("apple", "banana", "apple", "orange");
List<String> result = new ArrayList<>();

for (String s : list) {
    if (s.startsWith("a")) {
        result.add(s.toUpperCase());
    }
}
System.out.println(result);
```

* for, if, add 등 -> 어떻게 처리할지를 작성
* 조건, 필터링, 추가, 변환 -> 모든 절차를 명령
* 가독성 떨어지고, 작업이 복잡해질수록 코드량 증가



2. 선언형 프로그래밍

```java
List<String> list = Arrays.asList("apple", "banana", "apple", "orange");

List<String> result = list.stream()
                          .filter(s -> s.startsWith("a"))
                          .map(String::toUpperCase)
                          .distinct()
                          .collect(Collectors.toList());

System.out.println(result);
```

* 데이터가 어떻게 처리되는지는 Stream 관리
* 무엇을 하고 싶은지만 선언 -> a로 시작하는 것만 -> 대문자로 -> 중복제거
* 반복문 없음, 가공 흐름이 한눈에 보임
* 가독성, 유지보수성, 병렬처리까지 쉬워짐



⇒ 절차를 하나하나 명령하지 않고, 데이터 흐름만 선언하는 프로그래밍 방식

&#x20;
