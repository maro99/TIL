> Lean from yesterday, live for today, hope for tomorrow. The Important thnig is not to stop questioning                                                                                                                -Albert Einstein

### 작성 계획(19.5.25정정)

1. 블로그 처럼 글단위로 업데이트 한다.(개인 지식인 처럼 관리 하려함. 복습차원 + 질문해결관리)    
2. 그날배운토픽or 질문 따서각각  파일명 만든다.      
3. 하루 최소 1개 업데이트 
4. 질문 생각날시 README.md에 바로 업데이트  
5. 글작성 앞서서 respository검색해서 같은 토픽이면 그글 읽어보고 추가정보 업데이트 
6. 애매한것들 일단 알고있는 만큼 적어보고 추가로 찾아서 정보 기입    
7. 중요한데 안다고 생각하지만 설명 못하겠는것 모두 설명해 보기.     
8. 내용을 찾은것을 업로드 하다라도 한번 쭉 읽어보고, 그페이지안보고 설명해보기. 그뒤 수정하거나 내용 추가하도록하자.    
9. 댓글 달아가며 생각나는대로 최대한 복습 
### 질문 목록  
- token       
- rabbitmq vs reddis    
- 스케줄링시 nosql쓰는 이유          
- AWS 과금-ec2 free tier 사용중 언제 과금 많이 붙는지(db의 migration 자주 언급 되긴 했음.)     
- 현재 ec2한개만 써서 autoscaling 안쓰는데 이거 활성화 하는 방법은뭔지. 범위 설정 가능한지  
- AWS free tier 끝나고 다른 아이디 만들어서 프로젝트 옮길때 어떻게 할지    
- makemigration, migrate차이는    
- 현제 libarary\_movie 프로젝트 경우 api-server쪽에서 db 의 특정 table의 tuple 찾을때 field값 = @@ 이런 식으로 ORM 사용하는데 ORM 말고 sql로 직접 장고 프로젝트 상에서 작성하는 방법 사용해보자.     
- 내 프로젝트에서 정규화가 필요한 부분들은?   
- Movie.objects.filter(library\_library\_title\_ 이런식으로 튜플 검색시 효율 얼마나 떨어지는지?     
- Multi\_container\_docker   
- branch\_&\_enveronment\_in\_eb   
- url\_uri   
- HTTP응답상태코드   
- Django\_RESTFUL\_API      
- ElasticBenastalk 구조    
- ElasticBeanstalk 배포 전체 과정 설명해보기    
- 내프로젝트 구조도 그려보기     
- 웹서버 
- VPC,subnet,internetgateway.어떻게 분배 하나?   
- Route53   
- uwsgi랑 runserver랑 정확히 뭐가 같고 다른지? docker run시에 원래는 뒤에 runserver붙여서 했었는데 uwsgi를 supervisor로 돌리고 부터는 런서버 안해도 서버가 도네.  
-프론트 서버 python -m http.server 3000 으로 supervisor로 돌리는데 이거 문제 없나? 더좋은 방법은?   
- elb(443) -> ec2 -> ec2내부nginx-> container(7000) 인데 1) elb가 443으로 받은 요청을 어느 ec2에 줄지 어떻게 결정? 2) ec2내부nginx에서 어느 컨테이너로 갈지 어떻게 결정? (내경우 7000열어논거 자동으로 열린거 저거밖에라 들어가는건가?)  
- ORM, ORM 최적화   
- 디버거 세팅    
- 유저가 브라우져에 주소 첬을때 index페이지 보일때 까지 전체 과정 설명.   
- xss 공격
- 가상머신과 비교한 Docker 장점 
- 파이썬, 장고 버전 특징 

- (python) 추상클래스     
- (python) generator      
- (python) 모듈과 페키지 (11강 참조 )      
- (python) 클래스 메서드 (12강)   
- (python) 정적 메서드 (12강)   
- (python) 캡슐화 private,public, (12강)     
- (python) class (상속 등 및 기본 호출 ) (12강)      
- (python) decorator(12강)     

- 각 자료구조 언제 쓰고 특장점등 짚고 넘어가기 
- (datastructure) - 탐색트리 설명, 예제 손코딩  
- (datastructure) - 해쉬테이블 설명, 예제 손코딩    
- (datastructure) - 그래프 설명 및 예제 손코딩   
  
- (database) - 트랜잭션  24장 
- (database) - 트랜잭션 과 교착상태.방지법.-> 인터뷰깃 참고      
- (database) - 병행제어  26장    
- (database) - 무결성 27장       

- (os) - 프로세스와 스레드 ->84장      
- (os) - 스케쥴링 종류(장기, 중기,단기)  -> 85장  
- (os) - 스케줄링 기법(비선점,선점.fcfs등 ) -> 86,87장       
- (os) - 병행프로세스 88장     
- (os) - 교착상태(개요, 발생조건, 예방기법)89장   
- (os) - 기억장치(반입,배치,교체 및  할당기법<연속,분산-가상기억장치74장>)90~96장    
- (os) - 캐시의 지역성 (적중율등) 73장    
- (os) - 링커,로더등 처리프로그램 전체 흐름 77,83장     
  
- (network) - TCP/UDP
- (network) - TCP/IP 
- (network) - POST VS GET -> 인터뷰깃 
- (network) - IP 주소 체계 176장    
- (network) - 유저가 브라우져에 주소 첬을때 index페이지 보일때 까지 전체 과정 설명.-> 인터뷰깃, 177장,유튜브등 참고해서 어떻게든 완벽하게 설명해라 
- (network) - OSI7Layer   

- git 협업시 썼던것 회상.(clone받고, upstream설정, pull해서 최신화, 작업및 커밋후 pullrequest하던것 )   
- git branch등 나누고, 머지 하던 명령어 정리    

