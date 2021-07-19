### Git 충돌

다수의 개발자와 작업하다 보면 충돌이 생길 수 있다.
그럴땐 이 git 명령어를 입력하자.
```git
git stash && git pull origin <pull 할 branch> && git stash pop
```