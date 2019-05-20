## javascript 함수들을 동기적으로 동작 시키기 위해선 어떻게 하는게 좋을지?   

1. callback함수 사용.   
즉 함수 1, 함수 2 있으면 함수1의 내부의 맨끝(back)에서 함수 2를 호출(call)한다.    
```
function a(position) {

  console.log('function a called') 
  b();
}
```

2. async, await이용  
```
   async function init(){
     // alert('1')
     await a();
     // alert('2')
     await b();      
  }
```  



2번의 경우 await하는 함수안에 하위 함수 가 호출되 있을 경우 그 하위 함수가 끝난후에 그다음 await함수 (b)가 차례로 호출될 것이라는 보장은 없음
