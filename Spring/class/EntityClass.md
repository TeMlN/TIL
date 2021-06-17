### Entity Class란
#### domain package

* 실제 DB의 테이블과 매칭될 클래스
    * 즉, 테이블과 링크될 클래스임을 나타낸다.
    * Entity 클래스 또는 가장 Core한 클래스라고 부른다.
    * `@Entity`, `@Column`, `@Id` 등을 이용
* 최대한 외부에서 Entity 클래스의 getter method를 사용하지 않도록 해당 클래스 안에서 필요한 로직 method을 구현한다.
    * 단, Domain Logic만 가지고 있어야 하고 Presentation Logic을 가지고 있어서는 안된다.
    * 여기서 구현한 method는 주로 Service Layer에서 사용한다.
* 참고 Entity 클래스와 DTO 클래스를 분리하는 이유
    * View Layer와 DB Layer의 역할을 철저하게 분리하기 위해서
    * 테이블과 매핑되는 Entity 클래스가 변경되면 여러 클래스에 영향을 끼치게 되는 반면 View와 통신하는 DTO 클래스(Request / Response 클래스)는 자주 변경되므로 분리해야 한다.
    * Domain Model을 아무리 잘 설계했다고 해도 각 View 내에서 Domain Model의 getter만을 이용해서 원하는 정보를 표시하기가 어려운 경우가 종종 있다. 이런 경우 Domain Model 내에 Presentation을 위한 필드나 로직을 추가하게 되는데, 이러한 방식이 모델링의 순수성을 깨고 Domain Model 객체를 망가뜨리게 된다.
    * 또한 Domain Model을 복잡하게 조합한 형태의 Presentation 요구사항들이 있기 때문에 Domain Model을 직접 사용하는 것은 어렵다.
    * 즉 DTO는 Domain Model을 복사한 형태로, 다양한 Presentation Logic을 추가한 정도로 사용하며 Domain Model 객체는 Persistent만을 위해서 사용한다.
* 예시
```java
@Entity
@Getter
@AllArgsConstructor
@NoArgsConstructor
@EqualsAndHashCode
@ToString
public class User implements Serializable {
  private static final long serialVersionUID = 7342736640368461848L;

  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  @JsonProperty
  private Long id;

  @Column(nullable = false)
  @JsonProperty
  private String email;

  @Column(nullable = false)
  @JsonIgnore
  private String password;

  // @Override 
  // public boolean equals(Object o) { ... }
  // @Override
  // public int hashCode() { ... }
  // @Override
  // public String toString() { ... }
```