### *@ResponseBody 사용 원리* 

![ResponseBody](/img/ResponseBody.png)

* `@ResponseBody` 를 사용
* HTTP의 BODY에 문자 내용을 직접 반환 
* `viewResolver` 대신에 `HttpMessageConverter` 가 동작
* 기본 문자처리: `StringHttpMessageConverter`
* 기본 객체처리: `MappingJackson2HttpMessageConverter`
* byte 처리 등등 기타 여러 `HttpMessageConverter`가 기본으로 등록되어 있음 

> 참고: 클라이언트의 HTTP Accept 해더와 서버의 컨트롤러 반환 타입 정보 둘을 조합해서 `HttpMessageConverter` 가 선택된다.