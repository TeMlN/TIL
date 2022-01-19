### 결과 조회

*  fetch()
List로 조회, 데이터가 없으면 빈 List반환

<br>

* fetchOne()
단건 조회
    결과가 없으면 : `null`반환
    결과가 2개 이상 있으면 : `NonUniqueResultException` 반환

<br>

* fetchFirst()
첫번쨰 결과 한개만을 단건조회

<br>

* fetchResults()
페이징 정보 포함, total count 쿼리 추가 실행

<br>

* fetchCount()
count 쿼리로 변경해서 count 수 조회