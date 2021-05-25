## @CookieValue
* #### 쿠키 값을 parameter로 전달 받을 수 있는 방법이다.

* #### 해당 쿠키가 존재하지 않으면 500 에러를 발생시킨다.

* #### 속성으로 required가 있는데 default는 true다.
* #### false를 적용하면 해당 쿠키 값이 없을 때 null로 받고 에러를 발생시키지 않는다.

``` java
// 쿠키의 key가 auth에 해당하는 값을 가져옴
public String view(@CookieValue(value="auth")String auth){...}; 
```