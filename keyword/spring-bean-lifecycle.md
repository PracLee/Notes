# Spring Bean Lifecycle

1. **Instantiation (인스턴스화):**
   * Bean이 생성되는 단계,  일반적으로 XML 설정이나 Java Config 클래스에서 Bean을 정의하면, Spring 컨테이너는 해당 Bean을 인스턴스화
2. **Populate Properties (속성 주입):**
   * Bean의 속성들이 주입되는 단계, Setter 메서드나 필드 주입을 통해 Bean의 속성들이 설정
3. **BeanNameAware (Bean 이름 인지):**
   * Bean이 자신의 이름을 인식할 수 있도록 하는 단계, `BeanNameAware` 인터페이스를 구현하면, 컨테이너는 `setBeanName` 메서드를 호출하여 Bean의 이름을 전달
4. **BeanFactoryAware (Bean 팩토리 인지):**
   * Bean이 속한 Bean 팩토리를 인식하도록 하는 단계, `BeanFactoryAware` 인터페이스를 구현하면, 컨테이너는 `setBeanFactory` 메서드를 호출하여 Bean이 속한 팩토리를 전달
5. **PreInitialization (초기화 전):**
   * Bean이 초기화되기 전에 수행되는 단계, `InitializingBean` 인터페이스를 구현하거나 `init-method` 속성을 통해 초기화 메서드를 정의
6. **Initialization (초기화):**
   * Bean이 초기화되는 단계, 초기화 메서드가 호출되어 Bean을 사용할 준비
7. **PostInitialization (초기화 후):**
   * Bean이 초기화된 후에 수행되는 단계, `BeanPostProcessor` 구현체를 사용하여 초기화 후 작업을 추가
8. **Disposable (소멸):**
   * Bean이 소멸되는 단계, `DisposableBean` 인터페이스를 구현하거나 `destroy-method` 속성을 통해 소멸 메서드를 정의
