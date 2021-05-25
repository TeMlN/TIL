## @RequestBody
* #### 요청이 온 데이터(JSON이나 XML형식)를 바로 Class나 model로 매핑하기 위한 Annotation이다.

* #### POST나 PUT, PATCH로 요청을 받을때에, 요청에서 넘어온 body 값들을 자바 타입으로 파싱해준다.

* #### HTTP POST 요청에 대해 request body에 있는 request message에서 값을 얻어와 매핑한다.
* #### RequestData를 바로 Model이나 클래스로 매핑한다.

#### 이를테면 JSON 이나 XML같은 데이터를 적절한 messageConverter로 읽을 때 사용하거나 POJO 형태의 데이터 전체로 받는 경우에 사용한다.

``` java
@RequestMapping(value = "/book", method = RequestMethod.POST)
public ResponseEntity<?> someMethod(@RequestBody Book book) {
// we can use the variable named book which has Book model type.
    try {
    service.insertBook(book);
    } catch(Exception e) {
        e.printStackTrace();
    }

// return some response here
}
```