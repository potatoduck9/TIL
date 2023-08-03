# Copy, Shallow Copy, Depp Copy
> 객체의 복사 종류에는 Copy, Shallow Copy, Deep Copy가 있다.<br>
> 파이썬에서는 객체를 두 종류로 구분할 수 있다. mutable(변경되는 객체), immutable(변경되지 않는 객체) <br>
> mutable 객체의 종류는 list, set, dict 정도가 있고 immutable 객체의 종류는 int, float, str, bool 등이 있다. <br>
> immutable 객체는 copy와 크게 상관이 없지만 mutable 객체는 copy와 많은 관련이 있다.  

## 💡 mutable 객체와 copy의 관계 
> a 변수에 리스트(mutable) [1,2,3,4]를 할당하고, 변수 b에 a를 할당한 뒤에 b에 5를 추가한다. <br>
```python
a_list = [1,2,3,4]
b_list = a_list 
b_list.append(5) # b_list 5 추가 
print(a_list) # [1,2,3,4,5] 출력
print(b_list) # [1,2,3,4,5] 출력
```
> 위의 코드를 보면 변수 b에만 5를 추가했지만 a를 출력하면 변수 a에도 5가 추가된다. <br>
> 왜 변수 a에도 5가 추가됐을까? 위에 적었듯이 파이썬에서 list는 mutable 객체이기 때문에 변수 b에 a를 할당하면 같은 메모리 주소를 가지게 된다. <br>
> 즉 같은 메모리 주소를 가졌다는 건, 변수의 이름만 다르지 내용은 똑같다는 의미이기에 b에 5를 추가하면 a에도 5가 같이 추가된다. <br>
```python
print(id(a_list)) 
print(id(b_list))  # 변수 a와 b는 같은 id 값을 가진다. 
```
> 이처럼 변수의 값을 변경했는데, 원치 않게 같은 메모리 주소를 가지고 있는 다른 변수도 변경될 수 있기 때문에 이것을 방지하려면 shallow copy, deep copy를 사용해야 한다. <br>

## 💡 shallow copy 
> 변수 b를 변경했을 때 a가 변경되지 않게 하려면 shallow copy(얕은 복사)를 사용해야 한다. <br>
```python
import copy # copy 모듈 불러오기
c_list = [1,2,3, [4,5,6], [7,8]]
d_list = copy.copy(c_list) # copy 모듈 얕은 복사
print(id(c_list)) 
print(id(d_list)) # 일반 복사 방법과 다르게 얕은 복사를 사용한 변수 c와 d는 다른 id 값을 가진다.

d_list[1] = 100 
print(d_list)
print(c_list)  # 변수 d는  [1,100,3, [4,5,6], [7,8]]를 출력하고 변수 c는 리스트 값이 변경되지 않고 그대로 출력이 된다.
```
### shallow copy의 한계 
```python
d_list[3][1] = 200 # d_list의 3번째 리스트의 1번째 값을 200으로 변경
print(d_list) 
print(c_list) # c_list의 값은 변경하지 않았고 d_list의 3번째 리스트의 1번째 값만 200으로 변경하였지만 c_list도 d_list와 마찬가지로 값이 변경되었다. [1,2,3, [4,200,6], [7,8]] 출력 
```
> 위의 코드에서 알 수 있듯이 shallow copy는 리스트안에 또 다른 리스트의 값은 변경되는 문제가 있다. <br>

## 💡 deep copy
> shallow copy의 문제를 해결하기 위해 deep copy를 쓸 때도 있다.
```python
e_list = [1,2,3, [4,5,6], [7,8]]
f_list = copy.deepcopy(e_list) # copy 모듈 깊은 복사

f_list[4][1] = 300
print(f_list) 
print(e_list) # 변수 f는 [1,2,3, [4,5,6], [7,300]]을 출력했고 변수 e는 값이 변경되지 않고 그대로 출력이 된다. 
```
> 



