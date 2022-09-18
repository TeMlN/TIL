## All-Open

* #### open 키워드가 필요한 이유

Spring Boot 2.x 버전대부터는 CGLIB Proxy 방식으로 Bean을 관리하기 합니다. 여기서 CGLIB Proxy 방식을 사용하기 위해선 Target Class를 상속받아야 하기때문에 open으로 상속이 가능한 상태로 만들어줘야 하기 때문에 allOpen 키워드가 필요합니다. (코틀린은 기본적으로 모든 Class가 final로 정의됩니다.)