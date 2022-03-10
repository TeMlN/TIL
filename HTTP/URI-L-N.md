## URI, URL, URN

URI는 로케이터(**locator**), 이름(**name**)또는 둘다 추가로 분류될 수 있다.

![](/img/URI.png)

* URL : Resource, 즉 자원이 위치해 있는 곳
* URN : 자원의 이름 그 자체

![](/img/URN-URL.png)

### URI
* **U**niform : 리소스를 식별하는 통일된 방식
* **R**esource : 자원, URI로 식별할 수 있는 모든 것(거의 모든 것이 Resource이다.)
* **I**ndetifier : 다른 항목과 구분하는데 필요한 정보

### URL URN
* URL - Locator : 리소스가 있는 위치를 지정
* URN - Name : 리소스에 이름을 부여
* 위치는 변할 수 있지만, 이름은 변하지 않는다.
* URN 이름만으로 실제 Resource를 찾을 수 있는 방법이 보편화 되지 않음.

<br>

### URL의 전체 문법
* shceme://[userinfo@]host[:port][/path][?query][#fragment]
* https://www.google.com:443/search?q=hello&hl=ko

<br>

* shcem 
주로 프로토콜을 사용
http는 80포트 https는 443포트를 사용, 포트는 생략 가능
* userinfo
URL에 사용자 정보를 포함해서 인증
하지만 거의 사용하지 않음.
* host
호스트명
도메인명 또는 IP 주소를 직접 사용가능
* port
접속 포트
일반적으로 생략, 생략시 http는 80, https는 443으로 자동입력
* path
리소스 경로, 계층적 구조
예) /dotori/massage, /dotori/members, /dotori
* query
key=value 형태
?로 시작, &로 추가 가능 `?keyA=valueA&keyB=valueB`
query paramter, query string 등으로 불림, 웹서버에 제공하는 파라미터, 문자 형태
* fragment
html 내부 북마크 등에 사용
서버에 전송되는 정보는 아님