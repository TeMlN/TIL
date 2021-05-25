# @Controller 와 @RestController 의 차이
##  @Controller
* #### API와 view를 동시에 사용하는 경우에 사용한다.
    #### 대신 API 서비스로 사용하는 경우는 @ResponseBody를 사용하여 객체를 반환한다.
* #### view(화면) return이 주목적이다.

## @RestController
* #### view가 필요없는 API만 지원하는 서비스에서 사용한다.
* #### Spring 4.0.1부터 제공
* #### @RequestMapping 메서드가 기본적으로 @ResponseBody 의미를 가정한다.
    #### data(json, xml 등) return이 주목적이다.

#### 즉, @RestController = @Controller + @ResponseBody 이다.

