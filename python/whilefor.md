# While And For

## While
> while 조건문 :    
  &nbsp;&nbsp;&nbsp;수행할 문장1    
  &nbsp;&nbsp;&nbsp;수행할 문장2   
  &nbsp;&nbsp;&nbsp;수행할 문장3     
      
	  
### 예시
```python
>>> coffee = 10
>>> money = 300
>>> while money:
		print("돈을 받았으니 커피를 줍니다")
		coffee = coffee - 1
		print("커피가 %d 개 남았습니다." % coffee)
		if coffee == 0 :
			print("커피가 다 떨어졌습니다")
			break

```
* while 문 나갈때는 break 사용, while의 첫부분으로 돌아가고싶으면 continue     
     
	 
	 
	 
## for
> for 변수 in 리스트(또는 튜플, 문자열):    
	&nbsp;&nbsp;&nbsp;수행할 문장1    
	&nbsp;&nbsp;&nbsp;수행할 문장2    
		  
		  
### 예시
```python
>>>test_list = ['one','two','three']
>>>for i in test_list:
... 	print(i)
...

one
two
three

>>> a = [(1,2),(3,4),(5,6)]
>>> for(first, last) in a:
... 	print(first + last)
...
3
7
11	
```
      
	 
### for문과 range
```python
>>> a= range(10)
>>> a
range(0,10)

>>> add = 0
>>> for i in range(1,11):
		add = add + i
>>> print(add)
55
```
* a(10) : 0부터 10미만의 숫자를 포함하는 range객체를 만들어준다.     
* range(1,11) : 1부터 11미만의 숫자 range객체     
       
	   
### for 리스트 내포
```python
>>> a = [1,2,3,4]
>>> result = [num*3 for i in a if num%2 == 0]
>>> result
[6, 12]
```
* 짝수인경우에만 result 리스트에 담기    
