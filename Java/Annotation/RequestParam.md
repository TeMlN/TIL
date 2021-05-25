## @RequestParam
* #### @PathVariable과 비슷하다.
* #### request의 parameter에서 가져오는 것이다. method의 파라미터에 사용된다.
* #### ```?moviename=thepurge``` 와 같은 쿼리 파라미터를 파싱해준다.

* #### HTTP GET 요청에 대해 매칭되는 request parameter 값이 자동으로 들어간다.
    #### url 뒤에 붙는 parameter 값을 가져올 때 사용한다.
    ```http://localhost:8080/home?index=1&page=2```

``` java
@GetMapping("/home")
public String show(@RequestParam("page") int pageNum {
}
// 위의 경우 GET /home?index=1&page=2와 같이 uri가 전달될 때 page parameter를 받아온다.
@RequestParam //어노테이션의 괄호 안의 문자열이 전달 인자 이름(실제 값을 표시)이다.

@RequestMapping(value = "/search/movie", method = RequestMethod.GET)
public ResponseEntity<?> someMethod(@RequestParam String moviename) {
    // request URI would be like '/search/movie?moviename=thepurge'
    try {
    List<Movie> movies = service.searchByMoviename(moviename);
    } catch(Exception e) {
    e.printStackTrace();
    }
    // return some response here
}
```