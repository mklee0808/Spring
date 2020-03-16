# Spring Framework

##### Framework란?

 공통적인 부분, 반복적인 부분을 미리 만들어놓은 프로그램

 개발자는 프레임워크를 기반으로 소스코드를 작성하여 소프트웨어를 완성시키면 된다.

##### Spring?

 POJO기반의 경량 컨테이너

 Spring framework는 엔터프라이즈 애플리케이션 개발을 복잡한 EJB(Enterprise JavaBean)가 아닌 POJO(Plain Old Java Object, 자바로만 구성됨)를 통해서 개발 할 수 있도록 돕는다.  EJB보다 간단하게 이용할 수 있기 때문에 ''경량 컨테이너'' 라고도 부른다.

##### Spring 특징

- **OCP**(Open Closed Principle)   *개방폐쇄정책*

- **DI**(Dependency Injection) / **IoC**(Inversion of Control)

- **AOP**(Aspect Oriented Programming)

  > **OCP** :  인터페이스를 통해 제공되는 확장 포인트는 확장을 위해 개방되어 있고, 인터페이스를 이용하는 클래스는 자신의 변화가 불필요하게 일어나지 않도록 굳게 폐쇄되어 있다.
  >
  > **DI** : 객체간의 결합을 느슨하게 하는 스프링의 핵심 기술(constructor, setter, method)
  >
  > ​     IoC 컨테이너가 개발자 대신 `xml`파일에 정의된 대로 `bean`객체를 생성하고 의존성을 대신 주입하는 것
  >
  > **IoC** : 프로그램의 제어 흐름 구조가 뒤바뀌는 것

  > <img src="C:\Users\mk\AppData\Roaming\Typora\typora-user-images\image-20200316183950324.png" alt="image-20200316183950324" style="zoom: 67%;" />
  >
  > **AOP : ** 관점지향 프로그래밍의 중요한 개념은 ‘횡단 관점의 분리(Separation of Cross Cutting Concern)’ 이다.



- `pom.xml` : maven 설정파일, `dependency`를 사용해 필요한 파일들을 추가한다.

- `maven` : build, 배포를 관리해주는 `tool`

  [^build]: 코드 작성, 컴파일, 실행하는 일련의 과정들





1. `ApplicationContext`와 `ClassPathXmlApplicationContext`
   (상속관계) `BeanFactory` <- `ApplicationContext` <- `ClassPathXmlApplicationContext`
   스프링의 `ApplicationContext` 객체는 스프링 컨테이너(IoC컨테이너)의 인스턴스이다.
   스프링은 `ApplicationContext`의 몇가지 기본 구현을 제공한다.
   그 중 `ClassPathXmlApplicationContext`는 `XML` 형식의 독립형 어플리케이션에 적합하다.
   (지정된 `classpath`에서 `xml`파일을 읽어서 객체 생성)

```java
  ApplicationContext factory = new ClassPathXmlApplicationContext("com/test01/applicationContext.xml");
```



2. content, context, container
   content : 기능, 내용, ...
   context : 기능을 구현하기 위한 정보, 설정, ...
   container : 담는 그릇

  

3. 싱글톤 레지스트리
   스프링이 직접 싱글톤 형태의 오브젝트를 만들고 관리하는 기능을 제공한다.
   (스프링 `bean object`의 기본설정은 싱글톤이다.)

   [^싱글톤]: 메모리에 한번만 적재된다. 메모리에 객체 하나만 만들겠다.

   

4. 추상 클래스 생성 방법

   ```xml
   <bean id="singleton" class="com.test01.AbstractTest" factory-method="getInstance"></bean>
   ```

   추상 클래스는 기본 생성자(`new AbstractTest()`)로 바로 생성할 수 없어서 `factory-method` 속성을 통해 해당 객체를 생성해주는 메서드는 `getInstance`임을 알려준다

