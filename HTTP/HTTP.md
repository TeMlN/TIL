## HTTP (Hyper Text Transfer Protocol)

#### HTTP의 역사
* HTTP/0.9 1991년 : GET 메서드만 지원, HTTP 헤더X
* HTTP/1.0 1996년 : 메서드, 헤더 추가
* HTTP/1.1 1997년 : 가장 많이 사용, 우리에게 가장 중요한 버전
    * RFC2068 (1997) -> RFC2616(1999) -> RFC7230~7235(2014) 총 3번 개정
* HTTP/2 2015


### HTTP 메시지
![](/img/HTTP-request-message.png)
* start-line = **request-line** / status-line (요청 메세지는 request-line에 해당)
* **request-line** = method SP request-target SP HTTP-version CRLF

* CRLF = 줄바꿈 , SP = 띄어쓰기(공백)
<br>

* HTTP 메서드(GET, POST, PUT, DELETE)
* 요청대상 (/search?q=hello&hl=ko)
    - absolute-path[?query] (절대경로[?쿼리])
    - 절대경로 = "/"로 시작하는 경로
    - http://...?x=y 와 같이 다른 유형의 경로지정 방법도 있다.
* HTTP Version

![](/img/HTTP-response-message.png)

* start-line = request-line / **status-line** (응답 메세지는 status-line에 해당)
* **status-line** = HTTP-version SP status-code SP reason phrase CRLF

* CRLF = 줄바꿈 , SP = 띄어쓰기(공백)
<br>

* HTTP Version
* HTTP 상태 코드 : 요청 성공, 실패를 나타냄
    - 200: 성공
    - 400: 클라이언트 요청 오류
    - 500: 서버 내부 오류
* 이유 문구: 사람이 이해할 수 있는 짧은 상태 코드 설명 글

![](/img/HTTP-message-struct.png)

### Header
* header-field = field-name ":" OWS field-value OWS  (OWS: 띄어쓰기 허용)
* field-name은 대소문자 구문 없음
<br>

* 주의) `Host: www.taemin.com` 으로 예시를 들때 Host 다음에 띄워쓰기를 하고 :를 쓰면 안된다 `Host :`이런식으로 하면 안되고 `Host:`이렇게 붙혀서 써야한다 그리고 `Host`는 대소문자 구분을 하지 않지만 `field-value`인 `www.taemin.com`은 대소문자 구별을 한다

<br>

* HTTP 헤더의 용도
    - HTTP 전송에 필요한 모든 부가정보가 Header에 포함되어 있다
    - ex) 메세지 바디의 내용, 메세지 바디의 크기, 압축, 인증, 요청 클라이언트(브라우저)정보, 서버 애플리케이션 정보, 캐시 관리 정보 등등
    - 표준 헤더가 너무 많음
    - 필요시 임의의 Header 추가 가능
        * helloworld: hihi
 
