### MVC와 템플릿 엔진

* MVC : Model, Veiw, Controller

![MVC](/img/MVC.png)
 웹 브라우저에서 localhost:8080/hello-mvc 를 입력하면 내장 톰켓 서버가 스프링에게 요청을 넘기게 된다. 그럼 hello-mvc Controller가 리턴값으로 hello-template을 리턴하고, 동시에 model, 즉 key는 name이고 값은 spring인 model을 반환한다 그러면 리턴값인 hello-template를 templates 내에서 찾은후 hello-template.html을 웹 브라우저에 띄우게 된다.