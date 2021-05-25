## @Autowired
* #### 속성(field), setter method, constructor(생성자)에서 사용하며 Type에 따라 알아서 Bean을 주입 해준다.
* #### 무조건적인 객체에 대한 의존성을 주입시킨다.
* #### 이 Annotation을 사용할 시, 스프링이 자동적으로 값을 할당한다.
* #### Controller 클래스에서 DAO나 Service에 관한 객체들을 주입 시킬 때 많이 사용한다.

* #### 필드, 생성자, 입력 파라미터가 여러 개인 메소드(@Qualifier는 메소드의 파라미터)에 적용 가능하다.

* #### Type을 먼저 확인한 후 못 찾으면 Name에 따라 주입한다.