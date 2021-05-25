## @RequestHeader
* #### Request의 header값을 가져올 수 있다. 메소드의 파라미터에 사용한다.

``` java
//ko-KR,ko;q=0.8,en-US;q=0.6
@RequestHeader(value="Accept-Language")String //acceptLanguage 로 사용 
```