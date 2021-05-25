## @CacheEvict

* #### 캐시에서 데이터를 제거하는 트리거로 동작하는 method에 붙이는 Annotation이다.

* #### 캐시된 데이터는 언제가는 지워져야한다. 그러지 않으면 결과값이 변경이 일어났는데도 기존의 데이터(캐시된 데이터)를 불러와서 오류가 발생할 수 있다.

* #### 물론 캐시 설정에서 캐시 만료시간을 줄 수도 있다.

```java
@CacheEvict(value="cacheKey"), @CacheEvict(value="cacheKey", allEntries=true)
```

* #### allEntries는 전체 캐시를 지울지 여부를 선택하는 것이다. 