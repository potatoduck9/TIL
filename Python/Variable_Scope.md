# Variable Scope
> 파이썬에서는 변수가 선언된 위치에 따라 해당 변수가 영향을 미치는 범위까지 달라지며, 이것을 변수의 유효 범위(Variable Scope)라고 부른다. <br>
> 파이썬에서 지역변수란(local variable) 함수 내에서 선언된 변수를 의미한다.
> 파이썬에서 전역변수란(global variable) 함수 외부에서 선언된 변수를 의미한다. 


## 💡 Variable Scope EX1)
```python
a = 10 # global variable

def foo():
    # Local variable
    print('Ex1 > ', a) 

foo() # 지역변수에 값이 없으므로 전역변수인 10 출력 
# Read global variable
print('Ex1 > ', a)  # 전역변수 10 출력 

b = 20 # global variable

def bar():
    b = 30              # Local variable
    print('Ex1 > ', b)  # Read local variable

bar() # 지역변수 30 출력 

print('Ex1 > ', b)      # Read global variable


### 💡 Variable Scope EX2)
```python
c = 40 # global variable 

def foobar():
    # c = c + 10                   
    print('Ex2 > ', c)          

foobar()  # UnboundLocalError가 뜸
* * *

d = 50
def barfoo():
    global d # UnboundLocalError를 해결하기 위해 global 사용  
                 
    d += 100      
    print('Ex2 > ', d) # 150 출력

barfoo()    

print('Ex2 > ', d)     


#### 💡 Variable Scope EX3)
```python
def outer():
    e = 70
    def inner():
        nonlocal e # nonlocal 사용 
        e += 10 
        print('Ex3 > ', e)
    return inner
in_test = outer() 
in_test()          
in_test() # 값이 10씩 증가, Closure 패턴     

in_test = outer() # Closure 패턴 

in_test()          
in_test() # 값이 10씩 증가    
