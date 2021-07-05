### JPA 연관관계 매핑

#### 연관관계가 필요한 이유

> 전제조건
> * 회원과 팀이 있다.
> * 회원은 하나의 팀에만 소속될 수 있다.
> * 회원과 팀은 다대일 관계다.

#### 객체 테이블에 맞추어 모델링(참조 대신 외래 키를 그대로 사용)
![RelationMapping](/img/RelationMapping.png)

아래는 회원과 팀 클래스입니다.

```java
@Entity
public class Member {

  @Id @GeneratedValue
  private Long id;

  @Column(name = "USERNAME") 
  private String name;

  @Column(name = "TEAM_ID")
  private Long teamId;
  ...
  }

@Entity
public class Team {

  @Id @GeneratedValue
  private Long id;
  private String name;
  ...
  }
```

아래는 회원과 팀을 저장하는 코드입니다.

```java
//팀 저장
Team team = new Team();
team.setName("wooteco"); 
em.persist(team);

//회원 저장
Member member = new Member();
member.setName("conas");
member.setTeamId(team.getId());
em.persist(member);
```

이 상황에서 만약 회원의 팀을 찾으려면 어떻게 해야 할까요?

방법은 다음과 같습니다.

```java
Member findMember = em.find(Member.class, member.getId());

Long findTeamId = findMember.getId();
Team findTeam = em.find(Team.class, findTeamId);
```

연관관계가 없다면 위와 같이, member의 team을 가져오는데 계속 꺼내와야합니다.
member를 꺼내오고, id를 가져와서 다시 팀을 가져오는... 회원의 팀을 가져오기 위해 많은 비용이 듭니다.
그리고 객체 지향스럽지 않은 코드가 됩니다.

##### 객체를 테이블에 맞추어 데이터 중심으로 모델링하면, 협력 관계를 만들 수 없습니다.

* 테이블은 외래 키로 조인을 사용해서 연관된 테이블을 찾습니다.
* 객체 참조를 사용해서 연관된 객체를 찾습니다.
* 테이블과 객체 사이에는 이런 큰 간격이 있습니다.