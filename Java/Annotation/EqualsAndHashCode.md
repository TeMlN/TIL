## @EqualsAndHashCode
* #### equals와 hashCode method를 오버라이딩 해주는 Annotation이다.

```java
@EqualsAndHashCode(callSuper = true)
```

* ##### callSuper 속성을 통해 equals와 hashCode 메소드 자동 생성 시 부모 클래스의 필드까지 감안할지 안 할지에 대해서 설정할 수 있다.

* ##### 즉, callSuper = true로 설정하면 부모 클래스 필드 값들도 동일한지 체크하며, callSuper = false로 설정(기본값)하면 자신 클래스의 필드 값들만 고려한다.