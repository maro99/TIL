# 데이터 베이스에 자료를 저장하는 이유는? 왜 그냥 저장 안하지?   

.redis 정의를 살펴보면 redis는 메시지브로커로도 쓰이고 캐시로서의역할, 데이터베이스로서의 역할도 하는 데이터 자장소 이다. 라고
 되있다.

그렇다면 단지 데이터를 저장하는것과 데이터베이스는 어떤 차이가 있는지?
왜 단순히 disk에 저장안하고 데이터 베이스 거쳐서 저장하는지?

1. 질의어(SQL등)사용해서 데이터접근, 관리 쉽게할수 있다.
2. 데이터베이스 이용하면 데이터 look up 하는데 더 빠르다.
3. JOINS사용해서 두개의 다른 테이블 연관지을 수 있다.
4. 데이터베이스 안의 데이터들에 대한 유의미한 (경향?) 보고서를 만들 수 있다.
5. 데이터는 미리 만들어진 적합한 자료구조? 구조?가 정해져 있다.
6. ACID(원자성,일관성,고립성,지속성) 데이터베이스의 트랜젝션 안전하게 보장됨.
트랜젝션 = DBMS에서 상호작용 단위
7.아주 넓은 범위의 dataset을 다룰 수있다.
8. 동시에 많은 유저들이 db에 접속해서 정보 쓸 수 있다.
9. 크기변화 sacling 용이하다.



[참조](https://softwareengineering.stackexchange.com/questions/190482/why-use-a-database-instead-of-just-saving-your-data-to-disk)

