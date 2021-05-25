## @NoArgsConstructor
* #### 기본생성자를 자동으로 추가한다.

```java
@NoArgsConstructor(access = AccessLevel.PROTECTED)
```

* #### 기본생성자의 접근 권한을 protected로 제한한다.
* #### 생성자로 protected Posts() {}와 같은 효과

* #### Entity Class를 프로젝트 코드상에서 기본생성자로 생성하는 것은 금지하고, JPA에서 Entity 클래스를 생성하는것은 허용하기 위해 추가한다.

