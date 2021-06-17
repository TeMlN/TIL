### DTO(Data Transfer Object) 란?
#### dto package

* 계층간 데이터 교환을 위한 객체(Java Beans)이다.
    * DB에서 데이터를 얻어 Service나 Controller 등으터 보낼 때 사용하는 객체를 말한다.
    * 즉, DB의 데이터가 Presentation Logic Tier로 넘어오게 될 때는 DTO의 모습으로 바껴서 오고가는 것이다.
    * 로직을 갖고 있지 않는 순수한 데이터 객체이며, getter/setter 메서드만을 갖는다.
    * 하지만 DB에서 꺼낸 값을 임의로 변경할 필요가 없기 때문에 DTO클래스에는 setter가 없다. (대신 생성자에서 값을 할당한다.)
* Request와 Response용 DTO는 View를 위한 클래스
    * 자주 변경이 필요한 클래스
    * Presentation Model
    * toEntity() 메서드를 통해서 DTO에서 필요한 부분을 이용하여 Entity로 만든다.
    * 또한 Controller Layer에서 Response DTO 형태로 Client에 전달한다.
* 참고 VO(Value Object) vs DTO
    * VO는 DTO와 동일한 개념이지만 read only 속성을 갖는다.
    * VO는 특정한 비즈니스 값을 담는 객체이고, DTO는 Layer간의 통신 용도로 오고가는 객체를 말한다.
* 예시
```java
@Getter
@NoArgsConstructor
@AllArgsConstructor
public class UserDto {
  @NotBlank
  @Pattern(regexp = "^([\\w-]+(?:\\.[\\w-]+)*)@((?:[\\w-]+\\.)*\\w[\\w-]{0,66})\\.([a-z]{2,6}(?:\\.[a-z]{2})?)$")
  private String email;

  @JsonIgnore
  @NotBlank
  @Size(min = 4, max = 15)
  private String password;

  @NotBlank
  @Size(min = 6, max = 10)
  private String name;

  public User toEntity() {
      return new User(email, password, name);
  }

  public User toEntityWithPasswordEncode(PasswordEncoder bCryptPasswordEncoder) {
      return new User(email, bCryptPasswordEncoder.encode(password), name);
  }
}
```
