### ModelMapper 란?

다른 클래스로 어떠한 object가 갖고 있는 필드 값들을 쉽게, 자동으로 mapping 해주는 라이브러리 이다.

대부분의 필드들, 이름과 자료형이 같다면 getter, setter를 통해 자동으로 값을 복사해 주거나, 복사한 object를 만들어 주며, 완전히 동일하지 않더라도 규칙 설정을 통해 자동으로 매핑하도록 할수도 있고, 완전 다른 경우에는 커스터마이징을 통해 각 필드별로 수동으로 매핑 설정을 해줄 수도 있다.

<br>

#### 그렇다면 왜 ModelMapper를 사용해야 할까?
* 개발자들의 귀찮음
* 실수를 줄이기 위해

가장 큰 이유는 귀찮으니까 쓴다. 웹 어플리케이션 뿐만 아니라, input과 output과 repository에 저장되는 data의 모델링이 다른 경우가 많고, 그렇다면 결국 다른 모델의 object를 변환해줘야 하는 작업이 빈번하게 발생한다.

필드 한두개 쯤이야, 그냥 get/set 으로 쓰겠지만, 어디 우리가 하는 일이 그러한가? 20개쯤은 되어 줘야 일 하는 느낌이 들지.. 이렇게 get/set으로 노가다 매핑을 반복하다 보면, 빼먹는 필드들 한두개쯤 자연스레 생기고, 침침한 눈으로 눈알 빠지게 어느 필드 빼먹었나 찾아보게 되는 상황이 발생한다.

자동으로 매핑하면 이런 실수를 줄일 수 있게 도와준다.

<br>

#### 언제 써야 하죠?

예를 들어, 내가 회사에서 진행하는 프로젝트에서, view layer에서 사용하는 data의 형태는 dto라고 이름 붙여서 사용하는데, 이는 repository에서 사용하는 entity class 형태와 필드 대부분은 동일하나, 다른 형태로 구성되어 있다. 결국 repository에서 불러온 entity object는 dto 형태로 매핑해서 controller를 통해 응답하게 되고, 반대로 put이나 post 같은 경우, controller에서 받은 dto object를 entity 형태로 변환해야 한다.

<br>

#### 어떻게 사용하나요?

첫번째 의존성 주입을 한다 (maven, gradle)

* Gradle
```groovy
compile group: 'org.modelmapper', name: 'modelmapper', version: '2.3.0'
```

* Maven
```groovy
<dependency>
  <groupId>org.modelmapper</groupId>
  <artifactId>modelmapper</artifactId>
  <version>2.3.0</version>
</dependency>
```

* 설정 (Spring Bean으로 등록해두면 사용하기 용이하다)
```java
@Configuration
public class UserMapper {
    private final ModelMapper modelMapper = new ModelMapper();
    @Bean
    public ModelMapper userMapper() {
        // 매핑 전략 설정
        modelMapper.getConfiguration()
                .setMatchingStrategy(MatchingStrategies.STRICT);
        modelMapper.createTypeMap(User.class, UserDTO.class)
                .addMapping(User::getName, UserDTO::setUserName);
        return modelMapper;
    }
}
```

* 실사용 예제
```java
// 새로운 객체로 생성. user 를 userDTO로 변환
UserDTO userDTO = userMapper.map(user, UserDTO.class);
// 기존 객체에 매핑
userMapper.map(user, userDTO);
```