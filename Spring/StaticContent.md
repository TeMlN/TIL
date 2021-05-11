### 정적 컨텐츠

![staticContent](/img/staticContent.png)

웹 브라우저에서 localhost:8080/hello 입력하면 내장 톰켓 서버가 요청을 받게된다.  그후 내장 톰켓서버는 스프링에게 넘긴다. 그후 스프링은 먼저 controller쪽에서 hello-static이 있는지 먼저 찾게된다. 만약 controller쪽에 hello-static이 없으면 static쪽에서 찾게된다. 이 예제애선 static에 hello-static이 있기때문에 톰켓서버는 이 정적파일을, 즉 static(정적)파일을 웹브라우저에 전송을 하기때문에 정적 컨텐츠의 동작이 이루어지는 것 이다.
