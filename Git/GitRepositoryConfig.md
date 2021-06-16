## GitRepository의 구성

* #### Upstream Remote Repository (개발자들이 공유하는 저장소로 최신 소스코드가 저장되어 있는 원격 저장소 입니다)
* #### Origin Remote Repository (Upstream Remote Repository 를 fork한 원격 개인 저장소입니다)
* #### Local Repository (사용자의 개인 Repository, 개인의 Workspace라고 생각하면 편합니다)

![GitRepository](/IMG/GitRepository.png)

* #### 위 그림은 Git Repository 구성과 워크플로우를 설명하고 있습니다. 

<br>

* #### 순서는 이러합니다.
    * ###### Local Repository에서 작업을 완료한 한 후 작업 브랜치을 Origin Repository에 push
    * ###### Github에서 Origin Repository에 push한 브랜치를 Upstream Repository로 merge하는 Pull Request를 생성하고 코드리뷰를 거친 후 merge 
    * ###### 다시 새로운 작업을 할 때 Local Repository에서 Upstream Repository를 pull