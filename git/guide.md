# 마크다운 작성법

## Header
```c
# This is a H1
## This is a H2
### This is a H3
```
### 예시
# This is a H1
## This is a H2
### This is a H3


## BlockQuote
```c
	> This is a first blockqute.
	>> this is a second bolckqute
```
### 예시
> This is a first blockqute.
	>> this is a second bolckqute


## 목록
```
	1. 첫번째
	2. 두번째
```
### 예시
1. 첫번째
2. 두번째
	

```
	* 빨강
	 * 녹색
	  * 파랑
	 
	+ 빨강
	 + 녹색
	  + 파랑
	  
	- 빨강
	 - 녹색
	  - 파랑
```

### 예시
* 빨강
 * 녹색
	* 파랑
 
+ 빨강
 + 녹색
	+ 파랑
  
- 빨강
 - 녹색
	- 파랑

## 코드블럭

```java
		public class BootSpringBootApplication {
		  public static void main(String[] args) {
			System.out.println("Hello, Honeymon");
		  }

		}
```


## 수평선
```
* * *

***

*****

- - -

---------------------------------------
```
### 예시
---


## 외부링크
```
[링크](http://url "링크 설명- 마우스 hover시 나타는 설명문구)"
```
### 예시
[google](http://www.google.co.kr "구글")
   
    
	
## 이미지 넣기	
```
![이미지 이름](이미지 URL)
```   
   
git에 img폴더를 만들고 링크해주면 편하다.   
### 예시  
![ex_screenshot](./img/screenshot.png)   
   
    
## 표   
```
|제목|내용|설명|
|----|---|---|
|테스트1|테스트2|테스트3|
```   
   
### 예시   
|제목|내용|설명|
|----|---|---|
|테스트1|테스트2|테스트3|   