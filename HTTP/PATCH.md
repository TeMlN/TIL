## PATCH

* 리소스 부분변경


만약 /members/100에
```json
{
    username: taemin
    age: 19
}
```
라는 json 데이터들이 있다는 가정하에
/members/100에 
```json
{
    age: 16
}
```
으로 PATCH 전송을 한다면 members/100에는 
```json
{
    username: taemin
    age: 16
}
```
해당 json 정보들이 존재한다 즉 `부분변경`을 하는 것이다