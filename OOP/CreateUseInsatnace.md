### 인스턴스의 생성과 사용

###### [ClassAndInstance.md 에서의 예제를 다시 사용해보겠다](/OOP/ClassAndInstance.md)

![img](/img/classAndInstance.png)

#### 카드에는 아래와 같은 "속성(멤버변수)"와 "기능(메서드)"가 있다. 

* 1. 고객의 이름 (변수)
* 2. 카드 유효기간 (변수)
* 3. 카드 번호 (변수)
* 4. 정보 인식 기능 (메서드)
* 5. 정보 보안 기능 (메서드)

<br>

#### 고객마다 가지고 있는 정보가 다를 것이므로 서로 다른 생태를 갖게 하기 위해서 인스턴스를 생성한다.
```java
Card personA  =  new Card();

Card personB  =  new Card();

Card personC  =  new Card();
```

<br>

#### personA를 도식화 해보자.
![SchemaImg](/img/SchemaImg.png)

연산자 ( new )에 의해 : TV클래스의 인스턴스가 메모리의 빈 공간에 생성된다(0x100)

대입연산자(=)에 의해 : 생성된 인스턴스의 주소값이 참조변수 personA에 저장된다

* 참조변수 personA에 의해 인스턴스의 "멤버변수"와 "메서드"를 사용할 수 있게 된다.
* 사용하는 방법은 참조변수.변수명(or 메서드명)을 쓰면 된다.
```java
ex) personA.name = "홍길동"; , personB.name = "추신수"; , personC.name = "오승환";
```


