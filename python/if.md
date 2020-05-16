# 조건문
    
## if문
> if 조건문:    
	&nbsp;&nbsp;&nbsp;&nbsp;실행할 문장    
	&nbsp;&nbsp;&nbsp;&nbsp;실행할 문장    
  elif 조건문:    
	&nbsp;&nbsp;&nbsp;&nbsp;실행할 문장   
* 여기서 주의할점은 실행할 문장의 tab간격이 동일해야 함.   
* 아무것도 실행하고 싶지 않을땐 pass
    
### 예시
```python
>>> money = 2000
>>> if money >= 3000:
		print('택시타기')
	else:
		print('버스타기')
```
    
### X in s, X not in a
> x in 리스트    
x not in 리스트    
x in 튜플    
x not in 튜플    
x in 문자열   
x not in 문자열    
    
### 조건부 표현식
> 조건문이 참인경우 if 조건문 else 조건문이 거짓인 경우    

### 예시
```python
message = 'success' if score >= 60 else 'failure'
```