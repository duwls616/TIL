# java8의 lambda 표현식

> java8에 추가된 함수형 프로그래밍 요소이다.   
java8에는 람다표현식 말고도 스트림 API, java.time 패키지, 나즈혼 등이 추가되었는데 그중 하나인 람다표현식을 공부해보려 한다. 표현식은 다음과 같이 간단하다.   
   
(parameters) -> expression body
ex) Comparator comparator = (a, b) -> a.compareTo(b)   
() -> System.out.println("zero parameter");   
(a) -> System.out.println("one parameter" + a);   
(a, b) -> System.out.println("multiple Parameter" + a +","+ b);   
   
    
## 특징  
1. 타입선언이 선택적이다.   
2. 싱글 파라미터의 경우 괄호가 필요 없다.   
3. 중괄호 선택 : 한문장일 경우 중괄호가 필요 없다.   
4. return 키워드 : 한문장일 경우 생략 가능하다. 다만 중괄호를 포함한경우 무조건 return을 포함해야 한다.   
   
   
## 예제 

1. Lambda를 이용한 List 출력   
```java
ArrayList<Integer> arr = new ArrayList<Integer>();
arr.add(1);
arr.add(2);
arr.add(3);
arr.add(4);

arr.forEach(n -> System.out.println(n));

arr.forEach(n ->{if(n%2==0) System.out.println(n);});
```
   
output:
```java
1
2
3
4
2
4
```
    
forEach문을 사용하여 손쉽게 리스트를 다룰 수 있다.   

2. Lambda를 이용한 interface 사용   
```java
public class Test{
	
	interface FuncInter1{
		int operation(int a, int b);
	}
	
	interface FuncInter2{
		void sayMessage(String message);
	}
	
	private int operate(int a, int b, FuncInter1 fun){
		return fun.operation(a, b);
	}
	
	public static void main(String args[]){
		FuncInter1 add = (int x, int y) -> x + y;
		
		FuncInter1 mul = (int x, int y) -> x*y;
		
		Test tobj = new Test();
		
		System.out.println("Addition is "+ tobj.operate(6, 3, add));
		
		System.out.println("Multiplication is "+ tobj.operate(6, 3, mul));
		
		FuncInter2 fobj = message -> System.out.println("Hello " + message);
		
		fobj.sayMessage("Geek");
		
	}
}
```
   
   
output :
```java
Addition is 9
Multiplication is 18
Hello Geek
```
   
   
- expression body가 한줄인 경우 괄호 생략 가능하고 익명함수의 return 값은 body expression값과 같음
   
    
	[참조] https://www.geeksforgeeks.org/lambda-expressions-java-8/