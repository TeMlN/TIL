### DAO(Data Access Object) 란?
#### repository package

* 실제로 DB에 접근하는 객체이다.
    * Persistence Layer(DB에 data를 CRUD하는 계층)이다.

* Service와 DB를 연결하는 고리의 역할을 한다.
* SQL를 사용(개발자가 직접 코딩)하여 DB에 접근한 후 적절한 CRUD API를 제공한다.
    * JPA 대부분의 기본적인 CRUD method를 제공하고 있다.
    * ``` extends JpaRepository<User, Long>```
* 예시(JPA 사용 시)
```java
public interface QuestionRepository extends CrudRepository<Question, Long> {
}
```