# BeanFactory & ApplicationContext

*   BeanFactory

    * 빈을 생성하고 의존관계를 설정하는 기능을 담당하는 가장 기본적인 IoC Container
    * Spring Bean Container에 접근하기 위한 최상위 Interface
    * SpringBean을 관리하고 조회하는 역할
    * getBean()을 제공
    * Lazy-loading 방식을 사용

    \->  Bean을 사용할 때 로딩 (필요할 때만 로딩하기 때문에, 가벼운 경량 Container)



*   ApplicationContext

    * BeanFactory를 확장하고 있어 BeanFactory의 확장된 버전
    * Eager-loading 방식을 사용

    \-> Runtime 실행시 모든 Bean을 미리 로딩

    * MessageSource를 이용한 국제화 기능
    * EnviromentCapable 변수를 이용한 로컬, 개발, 운영 구분
    * ApplicationEventPublicher 애플리케이션 이벤트를 이용, 이벤트를 발행하고 구독하는 모델을 지원
    * ResourceLoader를 이용하여 편리하게 파일, classpath 등의 리소스를 조회
