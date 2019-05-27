요약: http 자체는 상태 인식 못한다. 하지만 우리는 장바구니에 물건 담고 돌아다니는 동안 그 정보가 지속되기를 원한다.  

## session Based Authentiaton:
유저가 로그인 한뒤 서버가 세션을 생셩한다.  
세션 id가 쿠키에 저장되고 유저가 로그인 상태로 있는동안  
이 쿠키가 모든 request에 담겨저서 보내질 것이다.  
그렇게하면 request를 받은 서버가  
쿠키에 담긴 session_id와 memmoriy(?)에 담긴 세션 정보를 비교해서  
유저의 신원을 확인하고   
그에 해당하는 알맞은 응답을 돌려준다.  

## Token Based Authentication  
많은 웹 어플리케이션이 json web token(jwt)를 authentication을 위해 쓴다. 세션 대신  
유저가 로그인을 시도하면  
서버가 secret으로 jwt를 만들고  
jwt를 클라이언트에게 보내준다.  
유저는 jwt를 (주로 local storage)에 저장하고  
앞으로 보내는 server로의 request의 header에 jwt를 붙여서 보낸다.  
서버는 jwd의 유효성을 검사호고 response를 보내준다.  
```
{  
  method: "GET",
  headers:{
    "Authorization": "Bearer ${JWT_TOKEN}"
  }
}
```


이런 식으로 나도 프로젝트에 토큰 추가했던것을 기억해라.  
  

차이점 ---->  
session과의 차이점은 users의 state 가 서버에 저장되지 않는다.  
대신 client쪽의 token에 유저의 상태가 저장된다.  
모바일인증 과, 확장성? 때문에 최근 jwt authenticate위해 많이 쓴다.  
(세션기반 인증 경우 세션이 서버 메모리에 담기기때문에 많은 수의 유저가 몰리면 문제가 될 수 있다.<세션 아이디만 로컬 쿠키에 가지고 있는다.> 반면 토큰 기반 인증의 경우 클라이언트 쪽에 토큰이 저장되기 때문에 유저수가 많이 늘어나는것(scaling)에 문제가 없다.
또한 쿠키를 여러 기기에 걸처서 공유할 수 없기에 다양한 기기에 로그인 유지 못하는데 토큰은 가능하기때문인듯???(핸드폰으로 유튜브 어디까지 봤는지 기록되고 컴퓨터에서 이어볼수 있는것 처럼)

[이글] (https://medium.com/building-contently/tracking-people-across-multiple-domains-when-cookies-just-arent-enough-b270cc95beb1) 읽으면 좋을것 같다.
