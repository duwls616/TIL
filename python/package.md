# 패키지
> 파이썬의 패키지는 디렉터리와 파이썬모듈로 이루어져 있다.      
game/     
&nbsp;&nbsp;____init____.py     
&nbsp;&nbsp;sound/     
&nbsp;&nbsp;&nbsp;&nbsp;__init__.py     
&nbsp;&nbsp;&nbsp;&nbsp;echo.py     
&nbsp;&nbsp;graphic/     
&nbsp;&nbsp;&nbsp;&nbsp;__init__.py     
&nbsp;&nbsp;&nbsp;&nbsp;render.py     
     
     
여기서 __init__.py 의 용도는 해당 디렉터리가 패키지의 일부임을 알려주는 역할을 한다.          
			
			
## 패키지 모듈 사용하기
1. import 사용하기	   
```python
>>> import game.sound.echo
>>> import game.sound.echo.echo_test()
```  
     
2. echo모듈이 있는 디렉터리까지 from...import 실행     
```python
>>> from game.sound import echo
>>> echo.echo_test()
echo
```
    
3. echo모듈의 echo_test 함수를 직접 import     
```python
>>> from game.sound.echo import echo_test
>>> echo_test()
echo
```

4. import *를 사용하기    
     
우선 echo패키지가 존재하는 패키지의 __init__.py 에 __all__ = ['echo']를 정의한다.    
* 를 사용하여 import 하는 경우 여기에 정의된 echo모듈만 사용한다는 뜻이다.    
```python
>>>from game.sound import *
>>>echo.echo_test()
echo
```     
     
5. relative 패키지     
```python
#render.py
from ..sound.echo import echo_test

def render_test():
		print('render')
		echo_test()
```
* 모듈안에서만 사용 가능