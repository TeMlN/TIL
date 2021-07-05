### 단방향 연관관계
회원과 팀의 관계를 통해 다대일 단방향 관계를 알아보겠습니다.

![UnidirectionalRelation img](/img/UnidirectionalRelation.png)

* 객체 연관 관계
    + 회원 객체(Member)는 Member.team 필드(멤버 변수)로 팀 객체와 연관관계를 맺습니다.
        * 회원 객체와 팀 객체는 단방향 관계입니다. 회원은 Member.team 필드를 통해 팀을 알 수 있지만, 팀 객체로 소속된  회원들을 알 수 없기 때문입니다. member ➡ team 의 조회는 member.getTeam()으로 가능하지만, team ➡ member 를 접근하는 필드는 없습니다.

<br>

* 테이블 연관관계
    + 회원 테이블은 TEAM_ID 외래 키로 팀 테이블과 연관관계를 맺습니다.

        * 회원 테이블과 팀 테이블은 양방향 관계입니다. 회원 테이블의 TEAM_ID 외래 키를 통해서 회원과 팀을 조인할 수 있고, 반대로 팀과 회원도 조인할 수 있습니다. 예를 들어, MEMBER 테이블의 TEAM_ID 외래 키 하나로 `MEMBER JOIN TEAM` 과 `TEAM JOIN MEMBER` 둘 다 가능합니다.
        * 회원과 팀을 조인하는 SQL
            ```sql
            SELECT *
            FROM MEMBER M
            JOIN TEAM T ON M.TEAM_ID = T.TEAM_ID
            ```

        * 팀과 회원을 조인하는 SQL
            ```sql
            SELECT *
            FROM TEAM T
            JOIN MEMBER M ON T.TEAM_ID = M.TEAM_ID
            ```

* 객체 연관관계와 테이블 연관관계의 가장 큰 차이
    참조를 통한 연관관계는 언제나 단방향입니다. 객체간에 연관관계를 양방향으로 만드록 싶으면 반대쪽에도 필드를 추가해서 참조를 보관해야 합니다. 이렇게 양쪽에서 서로 참조하는 것을 양방향 연관관계라고 합니다.
    하지만 정확히 이야기하면 이것은 양방향 관계가 아니라 서로 다른 단방향 관계 2개입니다. 반면에 테이블은 외래 키 하나로 양방향으로 조인할 수 있습니다.

<br>

* 객체 연관관계 vs 테이블 연관관계 정리
    + 객체는 참조(주소)로 연관관계를 맺습니다.
    + 테이블은 외래 키로 연관관계를 맺습니다.
    + 참조를 사용하는 객체의 연관관계는 단방향입니다.
    + 외래 키를 사용하는 테이블의 연관관계는 양방향입니다. (A JOIN B가 가능하면 반대로 B JOIN A도 가능)

<br>

### 연관관계 사용
#### Member, Team class

```java
@Entity
public class Member {

  @Id @GeneratedValue
  private Long id;

  @Column(name = "USERNAME") 
  private String name;

  @ManyToOne
  @JoinColumn(name = "TEAM_ID")
  private Team team;
  
  // Getter, Setter ...
}

@Entity
public class Team {

  @Id @GeneratedValue
  private Long id;
  private String name;
  
  // Getter, Setter ...
}
```

#### 연관관계 저장

```java
//팀 저장
Team team = new Team();
team.setName("TeamA");
em.persist(team);

//회원 저장
Member member = new Member(); 
member.setName("conas");
member.setTeam(team); //단방향 연관관계 설정, 참조 저장 
em.persist(member);
```

* 이전의 코드와 다른점은 member에 teamId를 넣지 않고, team을 넣어준다는 것입니다.

##### 참조로 연관관계 조회 - 객체 그래프 탐색

```java
//조회
Member findMember = em.find(Member.class, member.getId());
//참조를 사용해서 연관관계 조회
Team findTeam = findMember.getTeam();

```

##### 연관관계 수정

```java
// 새로운 팀B
Team teamB = new Team();
teamB.setName("TeamB");
em.persist(teamB);

// 회원1에 새로운 팀B 설정
member.setTeam(teamB);
```