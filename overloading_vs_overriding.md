# 오버로딩 vs 오버 라이딩 


## 상속(inheritance)  

> 부모클래스(super class) 의 기능을 자식클래스(sub class)가 물려받는것   

```
# 부모 클래스    
class Calculate():
	type = "low"  

	def __init__(self,n1,n2):
		self.n1 = n1
		self.n2 = n2 
	
	def sum(self):
		print(self.n1 + self.n2)   


# 자식클래스    
class Calculate\_1(Calculate):
	type = "high"
	
	def sub(self):
		print(self.n1-self.n2)  
	
	def mul(self):
		print(self.n1*self.n2)  
```
  
type을 high로 정의한 후 sub()함수와 mul()함수 기능을 추가했음    


## 다형성   
> 동일한 코드이지만 동작방법, 결과가 다른 것을 의미한다.

## 오버로딩(overloading)    
 
> "같은 클래스내에서 같은 이름의 메서드를 사용하는것"   

   
단 두가지 조건이 있음.    
1. 매개변수 타입 달라야 한다.(파이썬에서는 타입 없으니..유효안함. 변수이름 다르면될듯)     
2. 매개변수 개수가 달라야 한다.    

오버로드의 사전적 의미: 과부하, 과적하다.
-> 외울때 **같은 클래스에 한개더 과적해서 오버로드** 라 외우자.    

```
class Calculate\_2(Calculate\_1):
        type = "very high"

        def sub(self):
                print(self.n1-self.n2)

        def sub(self,pre_mul):
                print(pre_mul*self.n1-self.n2)

```



## 오버 라이딩(overriding)  

> "부모 클래스에서 정의한 메서드를 자식 클래스에서 변경하는것"      

상속이라는 개념이 사용됨.   



오버라이드의 사전적 의미: 무시하다. 기각하다.무효화하다.    
오버라이딩의 사전적 의미: 가장 최우선되는. 다른것보다 우선인    
-> 외울때 부모클래스의 메소드를  오버해서라이드 즉** 덮어 써서 오버라이드**라외우자.  
  
```
class Calculate\_2(Calculate\_1):
	type = "very high"

	def sub(self):
                print(self.n1-self.n2) 

	def mul(self):
		result = self.n1*self.n2)
		print('곱셈 결과는 %s입니다." %result)  

```
Caculate\1 을 부모클래스로써 상속을 받은 Calculate\_2클래스를 정의함.  
mul함수에 print를 하는 것을 추가해 재정의함 



