## @RequestMapping
* #### 요청 URL을 어떤 method가 처리할지 mapping해주는 Annotation이다.

* #### Controller나 Controller의 method에 적용한다.

* #### 요청을 받는 형식인 GET, POST, PATCH, PUT, DELETE 를 정의하기도 한다.

* #### 요청 받는 형식을 정의하지 않는다면, 자동적으로 GET으로 설정된다.

```java
@RequestMapping("/list"), @RequestMapping("/home, /about");
```

```java
@RequestMapping("/admin", method=RequestMethod.GET)
```

* #### PostMapping, GetMapping, @DeleteMapping, @PutMapping 으로 세분화 된다.