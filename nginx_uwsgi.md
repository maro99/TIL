# Nginx -uwsgi-django동작 구조     
![이미지](imgages/nginx_uwsgi.png)  

웹브라우저에서 웹서버로 http요청 보냄   
Nginx는 웹서버 로 맨앞에서 http 요청 받는다.   
Django의 Python 언어를 모르기 때문에 uWSGI는 HTTP요청 -> Python으로, 혹은 DJango로 받은 응답 -> Nginx가 알수있도록 변환해준다.       

좀더 자세히 설명해보면    
```

1.http 리퀘스트가 들어오면
2. 웹 서버가 그 리퀘스트를 받고,  서버사이드 처리가 필요 없으면 리스폰스를 리턴(static한 웹 서버)
3. 서버사이드 처리가 필요하면 wsgi 미들웨어를 통해 파이썬 어플리케이션으로 리퀘스트 전달
4. 파이썬 어플리케이션이 리퀘스트를 받아 처리 후 wsgi 미들웨어 - 웹서버를 통해 리스폰스 리턴.
의 구조라고 할 수 있다.  
```
정리하자면, 상식대로 **웹 서버 위에 서버 어플리케이션이 올라가는데 이 어플리케이션과 웹 서버간의 커뮤니케이션을 위해 wsgi 미들웨어가 존재하는 것** . 이 미들웨어를 어플리케이션을 적재하는 어플리케이션 컨테이너라고도 할 수 있다. 자바는 잘 모르지만, 자바 서블릿 컨테이너도 동일한 개념으로 보인다.



## uwsgi의 역할은?wsgi랑 뭐가 다르지?     
uwsgi는 WSGI(Web server gateway)를 구현한 것. 즉 wsgi의 한종류.  웹서버와 웹엡을 연결해주는인터페이스 정의해줌.-> 웹서버와 웹앱을 독립적으로 구성하게 해줌.(uwsgi이전에는 웹서버, 웹앱 선택에 제약있었다.)  


## docker run할때 runserver붙여줬을때는 uwsgi안썼던거 같은데 supervsor에서 uwsgi 를 실행해 주는것이 결국에는 runserver? 무슨 차이이지?   
django에서 runserver하던것은 django에서 코드를 자체적으로 테스트 하기 위한 간단한 웹서버를 갖고있던것을 테스트한것 이때 wsgi 사용됬다.   

재품 출시할때는 django에서 제공하는 간단한 웹서버를 사용하는것이 아닌, 보안이 더 좋고 강력한 웹서버가 필요해서 runserver말고 uwsgi를 사용해서 nginx와 연동한 방식을 쓰는것.      

(런서버로 배포시 가능은 하지만. 아무도 안쓰고 공식문서에서도 권장하지 않는다.)  
아래는 공식 문서에 적혀있는것.    
```
runserver [port or address:port]¶
django-admin runserver¶
Starts a lightweight development Web server on the local machine. By default, the server runs on port 8000 on the IP address 127.0.0.1. You can pass in an IP address and port number explicitly.

If you run this script as a user with normal privileges (recommended), you might not have access to start a port on a low port number. Low port numbers are reserved for the superuser (root).

This server uses the WSGI application object specified by the WSGI_APPLICATION setting.

DO NOT USE THIS SERVER IN A PRODUCTION SETTING. It has not gone through security audits or performance tests. (And that’s how it’s gonna stay. We’re in the business of making Web frameworks, not Web servers, so improving this server to be able to handle a production environment is outside the scope of Django.)
```


## nginx안쓰고 uwsgi만 쓸수는 없는지?   
가능하지만  Nginx가 가진 향상된 Static Contents(CSS, JavaScript 등) 핸들링을 통해서 서버에 발생되는 부하를 줄일 수 있기때문에 nginx앞단에씀.   정적 콘텐츠 처리와 사용자 요청을 위해 Apache, Nginx를 사용.    

## WAS? WEB SERVER? 
django server 와 같이, 프로그램 혹은 앱 단위의 로직을 처리하는 서버를 WAS(Web application server) 라고 하고, 앞단에 http request 를 처리하는 서버를 Web server 라고 한다

## 같이보면 좋을것들   
[CGI,WAS,WSGI](https://brownbears.tistory.com/350)

