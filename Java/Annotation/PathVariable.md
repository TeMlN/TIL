## @PathVariable
* #### method parameter 앞에 사용하면서 해당 URL에서 {특정값}을 변수로 받아 올 수 있다.

```java
@RequestMapping(value = "/some/path/{id}", method = RequestMethod.GET)
public ResponseEntity<?> someMethod(@PathVariable int id) {
}
```

* #### HTTP 요청에 대해 매핑되는 request parameter 값이 자동으로 Binding 된다.

* #### uri에서 각 구분자에 들어오는 값을 처리해야 할 때 사용한다.

* #### REST API에서 값을 호출할 때 주로 많이 사용한다.
    ```http://localhost:8080/index/1```

``` java
@PostMapping("/index/{idx}")
@ResponseBody
public boolean deletePost(@PathVariable("idx") int postNum) {
return postService.deletePost(postNum);
}
@RequestParam와 @PathVariable 동시 사용 예제

@GetMapping("/user/{userId}/invoices")
public List<Invoice> listUsersInvoices(@PathVariable("userId") int user,
	                                  @RequestParam(value = "date", required = false) Date dateOrNull) {
}
```

* #### 위의 경우 GET /user/{userId}/invoices?date=190101 와 같이 uri가 전달될 때
    #### 구분자 {userId}는 @PathVariable(“userId”)로,
    #### 뒤에 이어붙은 parameter는 @RequestParam(“date”)로 받아온다.