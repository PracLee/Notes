# Spring AOP(Aspect-Oriented Programming)

* 애플리케이션의 특정 관심사를 모듈화하고, 재사용할 수 있도록 해주는 프로그래밍 패러다임
* AOP는 주로 횡단관심사(로깅, 트랜잭션 관리, 보안)등을 처리



* Aspect (관점): 횡단 관심사를 정의하는 모듈, 여러 부분에서 사용될 수 있는 규칙들을 정의, 적용할 지점을 결정
*   Join Point (결합 지점): 특정 시점. Spring AOP는 여러 Join Point를 지원,

    \-> 메서드 호출, 객체 생성 등
*   Advice (조언): 결합 지점에 삽입되어 실행되는 코드 블록.

    \-> Before, After, Around 등 다양한 유형이 있으며, 각각 다른 시점에 실행
*   Pointcut (포인트컷): 결합 지점의 일부를 선택하는 표현식

    \-> Aspect는 어떤 Join Point에서 Advice를 실행할지를 결정하는 데 Pointcut을 사용
*   Target Object (대상 객체): Aspect를 적용할 실제 객체

    \-> 일반적으로 인터페이스를 구현,  클래스를 상속받은 것으로서, Aspect에 의해 부가적인 기능이 적용
