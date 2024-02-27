---
description: 객체를 직렬화, 역직렬화하는 라이브러리
---

# ObjectMapper

{% code title="변환할 객체" %}
```java
public class Person {
    private String name;
    private int age;

    // 기본 생성자, getter 및 setter 생략

    // 생성자
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

```
{% endcode %}

{% code title="직렬화" fullWidth="false" %}
```java
import com.fasterxml.jackson.databind.ObjectMapper;

public class ObjectToJsonExample {
    public static void main(String[] args) throws Exception {
        // ObjectMapper 생성
        ObjectMapper objectMapper = new ObjectMapper();

        // 예제 객체 생성
        Person person = new Person("John", 30);

        // 객체를 JSON으로 직렬화
        String json = objectMapper.writeValueAsString(person);

        // 결과 출력
        System.out.println(json);
    }
}

```
{% endcode %}

{% code title="역직렬화" %}
```java
import com.fasterxml.jackson.databind.ObjectMapper;

public class JsonToObjectExample {
    public static void main(String[] args) throws Exception {
        // ObjectMapper 생성
        ObjectMapper objectMapper = new ObjectMapper();

        // 예제 JSON 데이터
        String json = "{\"name\":\"John\",\"age\":30}";

        // JSON을 객체로 역직렬화
        Person person = objectMapper.readValue(json, Person.class);

        // 결과 출력
        System.out.println(person.getName()); // John
        System.out.println(person.getAge());  // 30
    }
}

```
{% endcode %}
