### @Id @GeneratedValue

* @Id

@Id 어노테이션이란 Entity Class 내에서 해당 프로퍼티가 기본키(primary key) 임을 나타내는 어노테이션 이다. 속성에 직접 @Id를 붙여주면 실행시점에 객체의 필드를 통해 직접 접근하게 하는 것이며, getter를 이용하려면 getter에 @Id를 붙여준다. 속성에부여하게 되면 setter/getter 없이도 작업이 가능하다. setter에 @Id를 붙이면 예외가 발생한다.
