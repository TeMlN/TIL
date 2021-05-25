## @Cacheable
* #### method 앞에 지정하면 해당 method를 최초에 호출하면 캐시에 적재하고 다음부터는 동일한 method 호출이 있을 때 캐시에서 결과를 가져와서 return하므로 method 호출 횟수를 줄여주는 Annotation이다.

* #### 주의할 점은 입력이 같으면 항상 출력이 같은 method(=순수 함수)에 적용해야한다.

* #### 그런데 또 항상 같은 값만 뱉어주는 메서드에 적용하려면 조금 아쉬울 수 있다.

* #### 따라서 메서드 호출에 사용되는 자원이 많고 자주 변경되지 않을 때 사용하고 나중에 수정되면 캐시를 없애는 방법을 선택할 수 있다.

``` java
@Cacheable(value="cacheKey"), @Cacheable(key="cacheKey")
```