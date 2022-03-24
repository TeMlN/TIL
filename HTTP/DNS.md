## DNS (Domain name server)

IP는 통상적으로 외우기 어렵습니다 또한 이 IP는 언제든지 바뀔 수 있습니다

#### DNS 란?
도메인을 등록하고 이 도메인을 IP 주소와 바꿀 수 있습니다.

예를 들어 도메인 명이 taemin.com 이고 이에 해당하는 IP가 200.200.200.2 라고 가정합니다

그리고 클라이언트가 taemin.com 에 접속을 하면 DNS 서버가 200.200.200.2의 IP주소를 뱉게 됩니다, 그리고 응답받은 이 IP 주소로 서버에 연결합니다. 만약 taemin.com 의 IP가 바뀐다면 어떻게 될까요? DNS 서버에서 taemin.com 도메인 명에 맞는 IP를 변경된 IP로 바꾸고 서버의 IP를 바꾸면 됩니다.

그래서 DNS는 기억하기 어려운 IP, IP가 변경되면 이라는 문제를 해결해 주는 것입니다.