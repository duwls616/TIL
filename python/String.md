# 문자열 자료형   
   
## 문자열 안에 따옴표 포함시키기   
```python
>>> food = "python's favorite food is perl"
python's favorite food is perl
>>> food = "python\s favorite food is perl"
python's favorite food is perl
```
   
    
## 여러줄 문자열을 대입할 때   
```python
>>> multiline = '''
... Life is good
... You need python
... '''
```   
'''은 """로 사용 가능   
   
## 문자열 연산   
```python
>>> head = "python"
>>> haed * 2
'pythonpython'
```   
   
## 문자열 길이
```python
>>> a = "Life"
>>> a.len()
4
```
   
## 문자열 인덱싱
```python
>>> a = "Life is too short, You need Python"
>>> a[3]
'e'
```

## 문자열 슬라이싱
```python
>>> a = "Life is too short, You need Python"
>>> a[19:-7]
'You need' 
>>> a[:1]
'L'
```
	
## 문자열 포맷팅
```python
>>> number = 10
>>> day = "three"
>>> "I ate %d apples. so I was sick for %s days." % (number, day)
I ate 10 apples. so I was sick for three days.
>>> "%10s" % "hi"
'          hi'  -> hi 오른쪽 정렬
>>> "%-10s" % "hi"
'hi          '  -> hi 왼쪽 정렬
>>> "%-10sjane" % "hi"
'hi          jane"
```

## 소숫점 표현
```python
>>> "%0.4f" % 3.424566
'3.4245'
>>> "%10.4f" % 3.424566
'    3.4245'
```
	
## format 함수 사용
```python
>>>"I eat {0} apples" .format(3)"
'I eat 3 apples'
>>>"I eat {number} apples" .format(number=3)"
'I eat 3 apples'
>>> "{0:<10}".format("hi")
'hi        '
>>> "{0:=^10}".format("hi")
'====hi===='
```
   
## f 문자열 포맷팅
```python
>>> name = "홍길동"
>>> age = 30
>>> f'내 이름은 {name}입니다. 나이는 {age}입니다'
내 이름은 홍길동입니다. 나이는 30입니다   
>>>d = {'name':'홍','age':30}
>>> f'내 이름은 {d["name"]}입니다. 나이는 {d["age"]}입니다'
```
		
## 위치알려주기
```python
>>> a = "Life is short"
>>> a.index('t')
8
>>> a.find('L')
0
```
			
## 문자열 삽입
```python
>>> ','.join('abcd')
'a,b,c,d'
```
	
## 공백지우기
```python
>>> a = "  hi  "
>>> a.strip()
'hi'
```