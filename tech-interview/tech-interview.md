## IoC (제어의 역전)
instance를 생성할때 의존성에 대한 제어권을 개발자가 아닌 spring이 하게 되는 것을 말합니다.
IoC 없이 instance를 생성할때 `Class instance = new Class()`이런식으로 하게 되는데 이럴경우 이 instance의 생명주기는 해당 class가 가지게 됩니다.
또한 생성된 instance의 대한 제어권은 해당 클래스가 가지게 됩니다.

말 그대로 제어의 역전입니다. 하지만 IoC를 이용한다면 인스턴스의 생명주기와 제어권은 IoC 컨테이너가 맡게 됩니다.

만약 IoC가 없다면 의존성에 대한 관리를 개발자가 직접 다 하는 상황을 맞이하게 될겁니다.

그럼 어떻게 spring이 의존성 주입을 해주는걸까요? 
정답은 IoC 컨테이너 입니다.

## IoC Container
IoC 컨테이너란 Bean으로 등록된 객체들을 관리하는 컨테이너입니다.

IoC 컨테이너는 ApplicationContext 또는 FactoryBean을 사용합니다 (ApplicationContext는 FactoryBean을 상속받습니다.)

참고로 의존성을 주입할때에 두 객체 모두 IoC 컨테이너에 등록되어 있어야 의존성 주입이 가능합니다. 

IoC 컨테이너의 기본 Scope는 SingletonScope이기 때문에 Singleton을 직접 구현하지 않아도 SingleTon 패턴을 사용할 수 있습니다.

## Bean
Bean이란 IoC 컨테이너가 만들어서 직접 그 안에 담고있는 객체입니다
즉 직접 추상클래스에 구현 클래스를 선언한 인스턴스는 Bean이 아닙니다. ex) `Member member = new Member();`

그러면 IoC 컨테이너에 Bean을 등록하려면 어떻게 할까요? 
어노테이션을 이용하면 됩니다.
`@ComponentScan`과 `@Bean`어노테이션으로 직접 등록해주는 방법이 있습니다. (`@Configuration` 등 Bean으로 등록되는 어노테이션 안에는 `@Component`가 존재함)

이후 `@Component`를 스캔하는 `@ComponentScan`어노테이션으로 `@Component` 어노테이션을 스캔해서 IoC 컨테이너에 Bean으로 전부 등록

직접등록 방법은 `@Bean`어노테이션을 이용해서 등록하거나 XML이나 자바 설정파일로 등록 (저자의 spring-core github repository에서의 AppConfig.class가 자바 설정 파일입니다.)

## DI 
Dependecy Injection, 의존성 주입
의존성 주입의 종류는 3가지가 있다.
* 생성자 주입
* 필드 주입
* 세터 주입

이 중 spring에서 권장하는 방법은 **생성자 주입**이다
