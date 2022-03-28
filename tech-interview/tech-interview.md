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
참고로 DI는 의존성을 **외부**에서 주입받는게 핵심이다
만약 서비스 로직에서 바로 인스턴스를 구현 클래스까지 할당하여 인스턴스를 생성한다? 이건 DI가 아닙니다. 하지만 추상 클래스부터 구현 클래스까지 정의 한 다음에 외부 클래스에서 생성한 이 인스턴스를 사용하는것은 DI가 맞습니다. 

## AOP
만약 수천만개의 메소드가 있는 프로젝트에서 각 메소드마다 성능을 측정하는 코드를 추가한다고 가정하자 처음에는 괜찮을 것이다 새로운 메소드를 추가할때만 추가하면 되니까.
하지만 여기서 로직의 변경으로 인해 성능만 측정해서 return 하는게 아니라 현재 시간까지 return 한다고 해보자 당신은 이 수천만개의 메소드에 일일히 하나하나 이 로직을 고칠 수 있는가? 절대 없다 하지만 다른 방법을 이용해 이 상황을 처리할 수 있다면?

그것이 바로 **AOP**이다.

AOP 구현 방법에는 3가지 방법이 있다.
* 컴파일
* 바이트코드 조작
* 프록시 패턴

컴파일 방법은 .java 파일이 .class가 되는 컴파일 시점에서 .class가 되기 전 중간에 이 성능측적 로직을 넣으면 된다 - AspectJ 에서 지원
바이트 코드 조작 방법은 .java 가 .class로 컴파일 되고나서 클래스 로더가 클래스를 읽을때 바이트 코드를 얻을 수 있는데 이 바이트 코드에다가 성능 측적로직을 넣으면 된다 - AspectJ 에서 지원
프록시 패턴은 Spring AOP가 사용하는 방법은 어노테이션을 만들어서 Aspect를 사용하거나 구현체를 2개 만들어서 사용해도 된다.

## PSA
우린 웹 백엔드 개발을 할때 서블릿 개발을 해야하지만 실질적으로 서블릿에 관한 코드를 작성하지 않는다.
왜일까
이유는 바로 Service Abstraction @Controller 어노테이션을 사용해서
@GetMapping, @PostMapping ..etc 등을 사용해서 서블릿을 추상화하여 사용하여서 비즈니스 로직에만 집중하면 된다.
그러면 Portable Serbice Abstraction은 무엇일까 바로 같은 기능을 사용하고 구현하지만 구현하는 웹 스택을 바꿀때 사용된다.

예시를 들자면 Spring MVC에서 tomcat 기반으로 MVC 개발을 하고있었다면 netty 기반으로 웹 스택을 바꿀 수 있다는 것이다 여기서 정말 중요한것은 기존 코드들을 조금만 손을 대거나, 손을 아예 대지않아도 이런게 가능하다는 것이다
```groovy
implementation 'org.springframework.boot:spring-boot-starter-web' -> implementation 'org.springframework.boot:spring-boot-starter-webflux'
```