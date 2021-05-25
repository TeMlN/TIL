## @CrossOrigin
* #### CORS 보안상의 문제로 브라우저에서 리소스를 현재 origin에서 다른 곳으로의 AJAX요청을 방지하는 것이다.

* #### @RequestMapping이 있는 곳에 사용하면 해당 요청은 타 도메인에서 온 ajax요청을 처리해준다.

``` java
//기본 도메인이 http://jeong-pro.tistory.com 인 곳에서 온 ajax요청만 받아주겠다.
@CrossOrigin(origins = "http://jeong-pro.tistory.com", maxAge = 3600)
```