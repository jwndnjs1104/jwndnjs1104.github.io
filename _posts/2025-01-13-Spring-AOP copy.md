---
title: Spring AOP
date: 2025-01-13 00:00:00 +09:00
categories: [Java, Spring]
tags:
  [
    Java,
    Spring,
    AOP
  ]
---


## **<span style="color: steelblue; visibility: hidden;">Spring AOP</span>**

### 1. AOP란?
![AOP](assets/img/Concept-of-AOP.png)
- Aspect Oriented Programming, 관점 지향 프로그래밍 방식
- 공통 관점(Cross-Cutting Concern, 횡단 관심사). 즉 보안,트랜잭션,예외처리 등 
  다른 클래스나 모듈에서 공통으로 필요한 기능을 분리하여
  필요한 모듈에 제공해 줌으로써 핵심관점(core concern)에만 
  집중 할 수 있도록 하는 프로그래밍 방식
- Spring AOP 프레임워크에서 이런 기능을 제공 해줌
- DI는 객체간의 결합도를 낮게 만드는 것이라면 AOP는 
  DI의 확장된 개념으로 공통적인 관점을 갖고 있는 
  개체들과의 결합도를
  낮게 만드는 것
- 즉, 코드의 간결함과 유지보수 편의성을 위한 것
- S**pring AOP**는 프록시 패턴 기반의 AOP



### 2. 왜 쓰는가?
- oop나 기존 프로그래밍에서는 상속이나 메서드 등으로 통해서
  공통 부분 등을 처리했으나  
  공통 부분이 수정이 되었을 경우 해당 공통부분을 호출하는 클래스들도 
  다시 수정하고 컴파일 해야하는 단점이 있다.  
  **AOP**는 공통 관심사항을 Spring의 AOP프레임 워크가 공통사항(공통관점)을 분리해 호출하고 
  DI패턴처럼 필요한 클래스나 모듈에 주입하게 된다.

### 3. AOP관련 용어
- Join Point: 메서드의 실행시점. 혹은 필드값 변경 등, 
                어느 위치를 기준으로 공통 모듈을 삽입하느냐.삽입지점
- Point Cut : 하나의 시작점 혹은 여러 시작점이 모여 Point Cut이 된다.  
    즉 하나의 Joint Point나 여러개의 Joint Point를 묶어서 Point Cut이라 함
- Advice: 실제 코딩의 단위로 Point Cut이 모여서 Advice가 된다.
          즉 중복되는 공통 관심사항을 따로 코드로 만들어 놓은 것.
- Advisor: 여러 Advice나 Point Cut이 모여 
              Advisor가 된다.
- Weaving: Advice를 핵심 로직코드에 적용하는 것을 
              위빙이라고 함. 즉 공통 코드를 핵심로직코드에 삽입하느것
- Aspect: 여러 객체에 공통으로 적용되는 공통관심사항
          트랜잭션이나 보안, 로깅등이 Aspect의 좋은 예


### 4. Advice의 종류
- @Before: 대상 객체의 메서드 호출전에 공통기능을 실행하는 Advice
- @AfterReturning: 대상 객체의 메서드가 예외 없이 실행된 후 실행되는 Advice
- @AfterThrowing: 대상 객체의 메서드를 실행하는 도중 
                                예외가 발생한 경우에 공통기능 실행하는 Advice
- @After: 대상 객체의 메서드를 실행하는 도중에 
예외가 발생했는지의 여부와 상관없이 메서드 실행 후 공통 기능을 실행하는 Advice
- @Around: 대상 객체의 메서드 실행 전/후, 또는 예외발생 시점에 공통기능을 실행하는 Advice

* 이들 중 범용적으로 사용되는 것은 @Around임.  
대상 객체의 메서드를 실행하기 전/후에 원하는 기능을 삽입 할 수 있기 때문

### 5. 스프링부트에서 적용법
- 현재 버전: 스프링 부트 3.xx  
  빌드 도구: gradle
1. pom.xml 설정에서 dependencies에 아래 dependency를 추가해준다.  

``` xml
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
  </dependency>
```

2. 위빙할 공통 코드가 있을 클래스에 @Aspect와 @EnableAspectJAutoProxy 어노테이션을 붙여서 AOP를 위한 프록시 객체를 생성할 수 있다.  
  > 사실 Spring Boot에서는 이 어노테이션을 사용하지 않아도 AOP가 활성화되어 있음  
  그래서 별도로 설정하지 않아도 로깅이나 트랜잭션 관리 같은 기능이 잘 돌아감  
  하지만, 명시적으로 AOP를 활성화하거나, AOP 동작 방식을 커스터마이징하고 싶다면 이 어노테이션을 사용해 AOP 동작을 제어할 수 있음

``` java
  @Aspect
  @EnableAspectJAutoProxy
  @Component
  public class CrossCuttingConcern {
    /*
      * 공통 관심 사항을 위빙할 타겟 클래스의
      * 어느 지점에 주입할 것인지 정의
      *
      * Pointcut설정시 execution명시자 형식의 문자열 지정
      *
      *  execution명시자:
      *  Advice를 적용할 패키지,클래스, 메서드를 표현할때 사용
      *  
      형식:execution(접근지정자패턴 리턴타입패턴 패키지이름패턴/클래스이름패턴/메서드이름패턴/(파라미터 패턴))
      =>AspectJ표현식이라고 함
    
      접근지정자패턴:생략가능(public, protected등)
      *:모든 값
      ..:0개 이상이라는 의미
      public * spring.aop..*(..)=>
      접근지정자가 public이고 모든 리턴타입에 대해 spring.aop패키지
      및 그 이하에 있는 모든 패키지의
      모든 클래스의 메서드에 대해 그리고 인자가 0개이상인 모든 메서드를 의미함.
      */
    
    /*
    * 공통 코드 메소드 작성 규칙
    * -반환타입:Object
    * -메소드명:임의로
    * -매개변수:ProceedingJoinPoint타입
    * -Throwable던져 준다.
    */
    @Around("execution(public * com.ictedu.spring.basic.aop..*(..))")
    public Object cuttingConcern(ProceedingJoinPoint point) throws Throwable {
      String coreConcern = point.getSignature().toShortString();
      System.out.println("대상 클래스의 핵심관점(메소드명): "+coreConcern);
      
      //[대상 클래스의 핵심 로직 실행전 수행할 공통로직]
      long startTime = System.currentTimeMillis();
      
      
      Object object = point.proceed(); //공통관점이 삽입된 핵심로직이 실행될때(위 패턴에 맞는 메소드 실행)
      
      
      //[대상 클래스의 핵심 로직 실행 후 수행할 공통로직]
      long endTime = System.currentTimeMillis();
      System.out.println(coreConcern+"의 총 실행시간: "+(endTime-startTime)/1000.0+"초");
      return object;
    }
  }
```



