@Value
properties에서 값을 가져와 적용할 때 사용한다.

@Value("${value.from.file}")

``` java
private String valueFromFile; //이라고 구성되어 있으면 value.from.file의 값을 가져와서 해당 변수에 주입해준다.
```
spEL을 이용해서 조금 더 고급스럽게 쓸 수 있다.

``` java
@Value(#{systemProperties['priority'] ?: 'some default'})
```