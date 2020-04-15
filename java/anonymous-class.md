# 익명클래스(Anonymous Class)   
   
> 이름이 없는 객체, 인터페이스를 구현하기 위해 해당 인터페이스를 구현하는 클래스를 생성해야하는데   
일회성이고 재사용할 필요가 없다면 익명클래스를 사용하면 된다.   
   
   
## 예시
```java
interface Info{
	public void print();
}


public class sampleClass{

	public static void main(String[] args){
	
		//익명객체
		Info info = new Info(){
			public void print(){
				System.out.println("seoul");
			}
		}
		info.print();
	}
}
```   
   
## 특징
1. 익명객체는 단독생성이 불가능하고 상속하거나 인터페이스를 구현해야만 사용가능
2. java8의 람다식의 대체로 사용할 수 있다.