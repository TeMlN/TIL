## H2 사용시 .mv.db 생성법

* h2 를 껐다 킨 뒤에 localhost:8082로 접속합니다
* JDBC URL 섹션에 jdbc:h2:~/"생성할 table명" 을 입력합니다
* 접속이 되었다면 jdbc:h2:tcp://localhost/~/"생성한 table명" 으로 접속하면 됩니다.