# AOP
핵심 로직은 아니지만 코드를 온전하게 만들기 위해서 필요한 부분   
예를 들어 파라미터가 올바르게 들어왔는지, 권한이 있는 이용자인지, 이 작업에서 발생할 수 있는 예외는 어떻게 처리할지와 같은 로직들   
이런 관심사를(cross-conern) 분리하여 공통적으로 작성함으로써 개발자는 핵심로직에만 집중할 수 있다.   
    
* 용어  	
   
Target : 핵심 비즈니스 로직   
Proxy : Target을 감싸고있는 부분, 외부에서 이 Proxy를 통해 Target객체의 JointPoint 를 호출한다.   
JoinPoint : Target이 가지고 있는 여러 메소드.   
Pointcut : Advice를 어느 Target에 적용할 것인지 결정하는 행위    
Advice : 적용할 관심사    
    
	   
	   
동작 위치에 따라 다음과 같이 구분된다.    
   
|구분|설명|
|----|--------|
|Before Advice|Target의 joinPoint를 호출하기전 실행된다. 코드 실행자체에는 관여할 수 없다.|
|After Returning Advice|모든 실행이 정상적으로 이루어진 뒤에 실행|
|After Throwing Advice|예외가 발생한 뒤에 실행|
|Ater Advice|정상적으로 실행되거나 예외가 발생했을 때 구분없이 실행|   
|Around Advice|메서드의 실행자체를 제어할 수 있다. 대상 메서드를 호출하고 결과나 예외를 처리할 수 있다|  
       
pointcut은 Advice를 어떤 JoinPoint에 결합할 것인지를 결정하는 설정이다.   
   
|구분|설명|
|----|-------|
|execution(@execution)|메서드를 기준으로 Pointcut을 설정|
|within(@within)|특정 타입을 기준으로 Pointcut을 설정|
|this|주어진 인터페이스를 구현한 객체를 대상으로 Pointcut을 설정|
|args(@args)|특정 파라미터를 가지는 대상들만을 Pointcut으로 설정|
|@annotation|특정 어노테이션이 적용된 대상들만을 Pointcut으로 설정|   
   
      
	   
## Advice 작성   
1. 간단한 로그기록   
```java
public class LogAdvice {
	@Before("execution(* org.zerock.service.SampleService*.*(..))")
	public void logBefore() {
		log.info("================");
	}
}
```
     
앞의 *은 접근제한자, 맨뒤의 *은 클래스의 이름과 메소드를 의미	 
    
2. 파라미터가 무엇인지 알고 싶을때 args를 이용하면 된다.   
```java
public class LogAdvice {
	@Before("execution(* org.zerock.service.SampleService*.doAdd(String, String)) && args(str1, str2)")
	public void logBeforeWithParam(String str1, String str2) {
		log.info("str1: "+str1);
		log.info("str1: "+str2);
	}
}
```
   
## @AfterThrowing  
지정된 대상이 예외를 발생한 후에 동작   
```java
@AfterThrowing(pointcut="excution(* org.zerock.service.SampleService*.*(..))", throwing="exception")
public void logException(Exception exception) {
	log.info("Exception!!!!!");
	log.info("Exception :"+exception);
}
```   
   
## @Around와 ProceedingJoinPoint
Around는 직접 대상 메서드를 실행할 수 있는 권한이 있고 실행 전과 실행 후에 처리가 가능하다.   
ProceedingJoinPoint는 @Around와 결합해서 파라미터나 예외등을 처리할 수 있다.   
```java
@Around("execution(* org.zerock.service.SampleService*.*(..))")
public Object logTime(ProceedingJoinPoint pjp) {
	long start = System.currentTimeMillis();
	log.info("Target: "+pjp.getTarget());
	log.info("Param :"+Arrays.toString(pjp.getArgs()));
	
	Object result = null;
	try {
		result = pjp.proceed(); //실행을 직접 관여
	}catch(Throwable e) {
		e.printStackTrace();
	}
	
	long end = System.currentTimeMillis();
	log.info("TIME: " + (end - start));
	
	return result;
}
```
ProceedingJoinPoint는 AOP대상이 되는 Target 이나 파라미터를 파악, 직접 실행을 결정할 수도 있다.   
메서드의 실행 결과를 직접 반환하는 형식으로 작성해야한다.     
Around 다음 Before 수행
   