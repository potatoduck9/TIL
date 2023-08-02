# Variable Scope
> 파이썬에서는 변수가 선언된 위치에 따라 해당 변수가 영향을 미치는 범위까지 달라지며, 이것을 변수의 유효 범위(Variable Scope)라고 부른다. <br>
> ex) 함수 내부에서 선언된 변수는(Local Variable)는 해당 함수 내부에서만 사용할 수 있으며 함수 밖에서는 사용할 수 없다. 


## Variable Scope EX1)
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
    print('Ex2 > ', b)  # Read local variable

bar() # 지역변수 30 출력 

print('Ex2 > ', b)      # Read global variable


### Variable Scope EX2)
```python
c = 40 # global variable 

def foobar():
    # c = c + 10   # UnboundLocalError가 뜸 
    # c = 10
    # c += 100
                 
    print('Ex3 > ', c)          

foobar()        

d = 50
def barfoo():
    global d # 전역 변수를 사용할 수 있음, 사용 자제 
                 
    d = 60       
    print('Ex4 > ', d)

barfoo()    

print('Ex4 > ', d)     


#### Variable Scope EX3)
```python
def outer():
    e = 70
    def inner():
        nonlocal e # nonlocal 사용 
        e += 10 # e = e + 10 
        print('Ex5 > ', e)
    return inner

in_test = outer() # Closure 패턴 

in_test()          
in_test() # 값이 10씩 증가    