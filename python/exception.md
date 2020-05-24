# exception
> try:     
    ...       
	except [발생오류[as 오류 메시지 변수]]:    
	...    
	   
## 오류 예외 처리 기법    
     
1. 모든 오류 발생시 except 문 실행    
```python
try:
   ...
except:
   ...
```   
    
2. 발생 오류만 포함한 except 문
:미리 정한 오류 발생시에만 except문 실행    
```python
try:
	...
except ZeroDivisionError:
	...
```	   
    
3. 발생오류와 오류 메시지 변수까지 포함한 except문
```python
try:
	...
except ZeroDivisionError as e:
	print(e)
```    

4. try, finally
```python
f = open("file.txt","w")
try:
	....
finally:
	f.close()
```    
    
5. 여러개 오류 가져오기
```python
try:
	...
except zeroDivisionError as e:
	print(e)
except IndexError as e:
	print(e)
```
     
     
## 오류 회피하기
```python
try:
	f=open("파일","r")
except FileNotFoundError:
	pass
```
    
    
## 오류 일부러 발생시키기
억지로 에러를 발생시키고 싶을때 raise 명령어 사용하면 된다.    
상속받는 클래스는 fly 메소드를 무조건 오버라이딩 시키고 싶을때    
```python
class Bird:
	def fly(self):
		raise NotImplementedError

class Eagle(Bird):
	pass
	
eagle = Eagle()
eagle.fly()
```
Eagle 클래스는 Bird 클래스를 상속받지만 fly 오버라이딩이 없어 NotImplementedError가 발생한다.    
     
## 예외 만들기
파이썬 내장클래스인 Exception 클래스를 상속하여 만들 수 있다.   
def \_\_str\_\_ 메서드는 print(e)처럼 오류메시지를 print문으로 출력할 경우 호출되는 메소드이다.(원하는 출력 메시지를 정할 수 있다)   
```python
class MyError(Exception):
	def __str__(self):
		return "허용되지 않는 별명입니다"
```
별명을 출력해주는 클래스
```python
def say_nick(nick):
	if nick == '바보':
		raise MyError()
	print(nick)
```
예외처리 기법을 사용하여 별명을 출력해보자    
```python
try:
	say_nick('바보')
	say_nick('천사')
except MyError as e:
	print(e)
```   
 