# Restful api란 ?  

##내머리속에 있는거 적어봄 :  
 restful\_api는 url을 지정할때 어떻게 규칙으로 지정할지 미리 정해놓을것.crud(create,read , update, delete) 연산 을 할때 어떤규>칙으로 할지 정해놓은것.자신만의 어떤 규칙이 아니라 일반적으로 보편적으로 생각할만한 방향으로 url 을 구성.

## 찾아본 내용:  
### **위키정의**
```
www같은 소프트웨어 아키텍쳐의 한형식.  
자원을 정의하고 자원에 대한 지정하는 방법 전반에 대한 패턴
```  

### **Rest란?**    
REpresentational State Transfer의 약자.  
즉 Rest의 기본 원칙을 지키는 (ful한)서비스 디자인.  
(uri동일한 같은 리소스 에서 상태의 변경이 representation들중 하나를 선택한 전송에 의해 이뤄진다는뜻. [참고](https://blog.npcode.com/2017/04/03/rest%EC%9D%98-representation%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80/))

### **REST 6 가지 원칙**  
(USCSC->   우리는 너를 (Arrest)하는 US-CSI(c)다 ! )  
   
1. **unifom**(유니폼 인터페이스):URI로 지정한 리소스에 대한 조작을 통일되고 한정적인 인터페이스로 수행( REST API는 **기본 URI와 미디어 타입의 정의만 알면 이용할 수 있어야**한다.예를 들어 Github API가 REST API라면, https://api.github.com 이라는 기본 URI와 application/json의 정의만 알면 API 문서 없이도 Github API 전체가 이용이 가능해야 한다는 말이 된다. 아마 가능하지 않을 것이다)    
2. **Stateless**(무상태성):작업을 위한 상태정보를 따로 저장하고 관리하지 않음. 세션 정보나 쿠키정보를 별도로 저장하고 관리하지 않기 때문에 **API 서버는 들어오는 요청만을 단순히 처리**.서비스의 자유도가 높고 구현이 단순.   
3. **Cacheable**(캐시가능):HTTP라는 기존 웹표준을 그대로 사용햬써 웹에서 사용하는 기존 인프라를 그대로 활용이 가능-> HTTP의 캐싱 기능 적용 가능.  
4. **Self-descriptiveness**(자체 표현 구조):REST API 메시지만 보고도 이를 **쉽게 이해** 할 수 있는 자체 표현 구조로 되어 있음     
5. **Client-server구조**: REST 서버는 API 제공, 클라이언트는 사용자 인증이나 컨텍스트(세션, 로그인 정보)등을 직접 관리하는 구조로 각각의 역할이 확실히 구분되기 때문에 클라이언트와 서버에서 개발해야 할 내용이 명확해지고 서로간 의존성이 줄어듬 .
6. **계층형 구조** :REST 서버는 다중 계층으로 구성될 수 있으며 보안, 로드 밸런싱, 암호화 계층을 추가해 구조상의 유연성을 둘 수 있고 PROXY, 게이트웨이 같은 네트워크 기반의 중간매체를 사용할 수 있게 함   
 
&nbsp  

### **RESTFUL하게 API를 디자인 한다는것**  

1. **리소스** 와 **행위** 를 명시적이고 직관적으로 **분리** 한다.(가장중요)  
 - 리소스는 URI로 표현되는데 리소스가 가리키는 것은 명사로 표현되어야 한다.(ex members)  
 - 리소스에 대한 행위는 HTTP Method로 표현하고, GET(조회), POST(생성), PUT(기존 entity 전체 수정), PATCH(기존 entity 일부 수정), DELETE(삭제)을 분명한 목적으로 사용한다.(ex POST /members/2 (o), GET/members/insert/2(x))   
 
2. **Message 는 Header 와 Body 를 명확하게 분리해서 사용한다** .  
 - **Entity** 에 대한 내용은 body 에 담는다.
 - 애플리케이션 서버가 행동할 판단의 근거가 되는 컨트롤 정보인 API 버전 정보, 응답받고자 하는 [MIME 타입](https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/MIME_types) 
 등은 header 에 담는다.
 - header 와 body 는 http header 와 http body 로 나눌 수도 있고, http body 에 들어가는 json 구조로 분리할 수도 있다.  

3. **API 버전을 관리한다.**  
 - 환경은 항상 변하기 때문에 API 의 signature 가 변경될 수도 있음에 유의하자.
 - 특정 API 를 변경할 때는 반드시 하위호환성을 보장해야 한다.(오픈 API를 제공하거나, 클라이언트가 항상 최신 버전을 유지할 수 없는 환경이라면 서버에서 버전 협상을 지원해야함. 그렇게하면 최신 버전으로 업데이트가 되더라도 구 버전의 정보 요청에 하위 호환하게 하여 서비스 적용범위를 넓게 유지할 수 있음 [참고](https://spoqa.github.io/2012/02/27/rest-introduction.html))   
  
4. **서버와 클라이언트가 같은 방식을 사용해서 요청하도록 한다.**  
  - 브라우저는 form-data 형식의 submit 으로 보내고 서버에서는 json 형태로 보내는 식의 분리보다는 json 으로 보내든, 둘 다 form-data 형식으로 보내든 하나로 통일한다.( URI 가 플랫폼 중립적이어야 한다.)  


### **장점**   
Open API 를 제공하기 쉽다  
멀티플랫폼 지원 및 연동이 용이하다.  
원하는 타입으로 데이터를 주고 받을 수 있다.  
기존 웹 인프라(HTTP)를 그대로 사용할 수 있다.    

### **단점**   
사용할 수 있는 메소드가 4 가지 밖에 없다.  
분산환경에는 부적합하다.   
HTTP 통신 모델에 대해서만 지원한다.    

[출처0](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Development_common_sense)  
[출처1](https://meetup.toast.com/posts/92) 4번항목 REST API디자인 가이드 보시오   
[출처2](https://spoqa.github.io/2012/02/27/rest-introduction.html)    

