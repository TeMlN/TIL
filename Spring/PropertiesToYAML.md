### Spring에서 Properties 속성을 YAML으로 바꾸는 방법

#### 그전에 YAML이란?

- XML, C, 파이썬, 펄, RFC2822에서 정의된 e-mail 양식에서 개념을 얻어 만들어진 '사람이 쉽게 읽을 수 있는' 데이터 직렬화 양식.
<br>
- YAML은 모든 데이터를 리스트, 해쉬, 스칼라 데이터의 조합으로 적절히 표현할 수 있다는 믿음을 가지고 만들어졌다.
문법은 상대적으로 이해하기 쉽고, 가독성이 좋도록 디자인되었으며, 고급 컴퓨터 언어에 적합하다.
또한 들여쓰기 및 XML의 특수기호를 사용하기 때문에, XML과 거의 비슷 핟.
<br>
- JSON은 yaml의 일종이다.

#### 전환 방법

```properties
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5InnoDBDialect
spring.h2.console.enabled=true
spring.profiles.include=oauth
spring.session.store-type=jdbc
```
여기 한 properties 파일이 있다, 이 properties로 예를 들겠다.

우선 `.`으로 단위를 구분한다.
지금 이 properties 에선
`spring`, `jpa`, `show-sql`, `properties`, `hibernate` etc.. 가 있다

그럼 이 키워드들을 가지고 계층형(`yaml`)으로 전환해보자.

```yaml
spring:
    jpa:
        show-sql: true
        properties:
            hibernate:
                dialect: hibernate.dialect.MySQL5InnoDBDialect
    h2:
        console:
            enabled: true
    profiles:
        include: oauth
    session:
        store-type: jdbc
```
이런식으로 할수가 있다. 
<br>


이상 이 글을 마친다.
더 이상의 정보는 https://goddaehee.tistory.com/213 이 블로그를 참조하면 좋을 듯 하다.