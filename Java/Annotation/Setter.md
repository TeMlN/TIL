## @Setter

* #### Class 내 모든 필드의 Setter method를 자동 생성한다.

* #### Controller에서 @RequestBody로 외부에서 데이터를 받는 경우엔 기본생성자 + set method를 통해서만 값이 할당된다.

* ##### 그래서 이때만 setter를 허용한다.
* ##### Entity Class에는 Setter를 설정하면 안된다.
* ##### 차라리 DTO 클래스를 생성해서 DTO 타입으로 받도록 하자