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
