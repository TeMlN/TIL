## Cookie

쿠키는 두개의 헤더가 존재한다.
* Set-Cookie
* Cookie

Set-Cookie: 서버에서 클라이언트로 쿠키 전달(response)
Cookie: 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청시 서버로

* (토큰, Session등을 사용하지 않았을때의 예시)

martial이란 유저가 로그인한 유저의 이름을 반환하는 페이지에 접속했다 가정을 해보자
기댓값은 martial이란 String 타입의 문자열을 반환하는거겠지만 그렇지 않다

왜냐하면 서버는 해당 페이지에 접속한게 martial인지, guest인지 모르기 때문이다.

이를 해결하기 위한 방법하나가 바로 Cookie이다. 그러면
로그인 state에서 회원의 정보를 `Set-Cookie: user=martial`같이 key = value의 형태로
Cookie저장소에 저장을 한다.

이 과정을 거치면 브라우저에서 서버에 보내는 모든 요청에 Cookie가 포함된다.

하지만 Cookie가 모든 요청에 보내지면 보안상 문제가 생길 수 있기때문에 이를 제약하는 방법도 존재한다.