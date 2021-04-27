## Optional 이란?

##### `Optional`는 “존재할 수도 있지만 안 할 수도 있는 객체”, 즉, “`null`이 될 수도 있는 객체”을 감싸고 있는 일종의 래퍼 클래스입니다. 원소가 없거나 최대 하나 밖에 없는 `Collection`이나 `Stream`으로 생각하셔도 좋습니다. 직접 다루기에 위험하고 까다로운 `null`을 담을 수 있는 특수한 그릇으로 생각하시면 이해가 쉬우실 것 같습니다.

<br>
<br>

## Optional 왜 쓰는건데?

* ##### NPE를 유발할 수 있는 null을 직접 다루지 않아도 됩니다.
* ##### 수고롭게 null 체크를 직접 하지 않아도 됩니다.
* ##### 명시적으로 해당 변수가 null일 수도 있다는 가능성을 표현할 수 있습니다. (따라서 불필요한 방어 로직을 줄일 수 있습니다.)

## Optional 사용법은?
```java
Optional<Order> maybeOrder; // Order 타입의 객체를 감쌀 수 있는 Optional 타입의 변수
Optional<Member> optMember; // Member 타입의 객체를 감쌀 수 있는 Optional 타입의 변수
Optional<Address> address; // Address 타입의 객체를 감쌀 수 있는 Optional 타입의 변수
```