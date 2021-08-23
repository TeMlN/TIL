#### intellij 에서 갑자기 되던 임포트들이 임포트가 안될때

* 필자의 os인 macos 기준으로 작성합니다.

<br>

##### Command + Shift + A 를 누릅니다.
*   그 후 All 탭 바를 선택합니다.
##### classpath를 검색합니다.
![classpath](/img/classPathTabBar.png)
* 상단의 Obtain processors from project classpath 를 들어갑니다.
##### 그 후 
![enable](/img/EnableAnnotation.png)
* Enable annotation processing 체크박스를 체크 합니다.
* 그리고 Apply(신청) 버튼을 누릅니다.
* 기다립니다.

##### + build.gralde 잘 살펴보기 어느 순간 오류가 나길래 보아하니 build.gralde이 초기 상태로 돌아간 적이 있었다.

##### 짜잔 되셨나요?
  필자분들 모두 저처럼 삽질하지 않으셨음 합니다 하지만 제가 이 오류들을 고치기위해서 구글링을 1시간을 하였기 때문에 선행했던 일련의 과정들이 많습니다 최종적으로 이 방법을 실행한 후 해결이 되었기 때문에 먼저 이 글을 작성하려고 합니다 ㅠ 안되셔도 절대 포기 말아주세요 참고했던 블로그는 다 링크 남겨두도록 하겠습니다.

[최종적으로 오류를 해결할 수 있었던 방법 classpath](https://jsonobject.tistory.com/256)
[Add Framework Support](https://m.blog.naver.com/kiel0103/221766235162)
[Maven Importing](https://stackoverflow.com/questions/53869118/importing-to-intellij-error-package-org-springframework-boot-does-not-exist)

