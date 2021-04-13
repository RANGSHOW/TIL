# ***Spring Framework***

> ### 엔터프라이즈 애플리케이션 구축을 위한 솔루션

- 자바 애플리케이션 개발을 위한 포괄적인 인프라를 제공하는 자바 플랫폼
  - 스프링에서 인프라를 처리하므로 개발자는 애플리케이션 개발에만 집중
- 모듈화되어 있어서 필요한 부분만 사용 가능
- 완전한 기능을 갖춘 MVC 프레임워크 제공
- 국내에서는 자바 개발자들에게 표준 프레임워크로 자리 잡음



### 스프링 프레임워크 선행학습

- Java
- HTML / CSS / JavaScript / jQuery
- JSP & Servlet



## 스프링의 장점

- #### 생산성 우수

  - 엔터프라이즈 애플리케이션 구축을 위한 솔루션이지만

    가볍고 모듈화되어 있어서 필요한 부분만 사용

  - POJO 클래스와 약간의 설정만으로도 개발이 가능하므로 개발 생산성을 높일 수 있음
  - 스프링 적용하면 개발 코드를 1/3 정도의 코드만으로도 개발 가능





#### EJB (Enterprise JavaBean)

- 규모가 커지고 복잡한 애플리케이션 제작을 위해 만들어진 기술

- extends, implements를 많이 사용해서 클래스 의존도가 높고, 복잡하고 제한이 많은 문제 발생

  이러한 문제 때문에 별도로 종속되지 않는 간단한 자바 객체를 사용하자는 의도로 POJO 개발됨

#### POJO (Plain Old Java Object)

- 특정 환경과 규약에 종속되지 않고 필요에 따라서 재사용될 수 있는 방식으로 설계된 객체

  즉, 복잡하게 다른 클래스를 상속받거나 인터페이스를 구현해야 하는 규칙이 없는 자바 클래스

- POJO 대표적인 예
  - JavaBean: 생성자와 Getters / Setters 만 지닌 단순 자바 객체
- 대표적인 POJO 기반의 프레임워크
  - 스프링 프레임워크



- #### 품질 보증

  - 스프링 프레임 워크는 이미 검증된 많은 아키텍처 및 디자인 패턴을 적용해서 만들어졌기 때문에

    코드에 아키텍쳐 구현하기 위한 코드나 디자인 패턴을 사용하기 위한 코드를 개발자가 만들 필요가 없음

  - 개발에 일관성을 제공해주고 소프트웨어 품질 보증

- #### 유지 보수 용이

  - 스프링 프레임워크를 사용해서 작성된 애플리케이션은 유지보수에 소요되는 인력, 시간을 줄일 수 있음

    그래서 여러 프레임워크 중에서 스프링 프레임워크가 업계 표준으로 자리 잡음



---

## 스프링 프레임워크 특징

- 1) POJO 기반 프레임 워크
- 2) DI (Dependency Injection) 지원
- 3) AOP (Aspect Oriented Programming) 지원
- 4) 뛰어난 확장성
- 5) Model2 방식의 MVC Framework 지원
- 6) WAS(애플리케이션 서버)에 종속되지 않는 새발 환경



#### 1) POJO 기반 프레임 워크

- 자바 객체의 라이프 사이클을 스프링 컨테이너가 직접 관리
- 스프링 컨테이너로부터 필요한 객체를 얻어옴



#### 2) DI (Dependency Injection) 지원

- 의존성 주입

- 의존 관계에 있는 객체를 생성 조립해주는 기능

- 각 계층이나 서비스들 사이 또는 객체들 사이의 의존성이 존재할 경우 

  스프링 프레임워크가 서로 연결해줌

- 클래스 간의 약한 결합 가능

- A 클래스 B클래스 의 객체를 사용할 때

  지금까지는 B b = New B(); 	// 개발자가 필요할 때 언제든지 new 연산자를 사용해서 

  의존 관계가 있는 객체 생성 / 사용

- 스프링에서는 new 연산자로 마음대로 객체 생성 못함

  스프링 컨테이너가 만들어서 넣어주겠다는 의미



#### 3) AOP (Aspect Oriented Programming) 지원

- 관점 지향 프로그래밍
- 공통 기능을 분리해서 사용
  - 트랜잭션 로깅, 보안 등 여러 모듈에서 공통적으로 지원하고 기능을 분리해서 사용
- 반복적인 코드를 줄이고 개발자가 비즈니스 로직에만 집중할 수 있도록 지원



#### 4) 뛰어난 확장성

- 스프링 프레임워크의 소스는 모두 라이브러리로 분리되어 있어서

  필요한 라이브러리만 가져다 사용하면 됨

- web.xml 에 추가



#### 5) Model2 방식의 MVC Framework 지원

- Model / View / Controller
- JSP MVC 때 보다 코드가 간경

### 핵심 기능

- DI (Dependency Injection) 주입
  - 객체 간의 의존성을 개발자가 설정하는 것이 아니라
  - 스프링 컨테이너가 주입시켜주는 기능
  - 장점: 객체를 쉽게 확장하고 재사용할 수 있음
- loC (Inverdion of Control: 제어의 역전)
  - 객체에 대한 제어권 문제
  - 기존에는 개발자에게 제어원이 있었음: new 연산자 사용해서 마음대로 객체 생성 가능
  - 스프링 프레임워크에서는 객체의 제어권이 스프링에 있고
  - 인스턴스의 라이프 사이클 (생성에서 소멸까지)을 개발자가 아닌 스프링 프레임워크에서 담당
  - 제어권이 역전되었다고 표현함



---

### 개발 환경 구성

- JDK
- Spring Tools
  - STS (Spring Tool Suit) 사용: 이클립스에 스프링 플러그인이 포함된 버전 (이 방식 사용)
  - Eclipse에서 Spring Tools 플러그인 설치

- Tomcat
- Oracle Database 11g Release 2: Express Edition



#### 설치 및 환경 설정

- STS4 설치: Spring Boot만 설치
- Spring Tools 3 Add-On 3.9.16 추가 설치
- Eclipse Java EE Developer Tools 설치



먼저 Workspace 생성

- springWorkspace



STS4 다운로드

- 압축 해제시 이름이 너무 길다 (경로가 길다는 오류 발생)

- C: 또는 D: 로 이동
- 파일명을 sts.jar로 줄임

- sts.jar 압축해제
- contents.zip 압축해제
- sts-4.10.0.RELEASE 폴더 이동
- SpringToolSuite4.exe 실행 (작업 표시줄에 고정)

- Help → Eclipse MarketPlace에서 다음 검색해서 설치
  - Spring Tools 3 Add-On 3.9.16 추가 설치
  - Eclipse Java EE Developer Tools 설치
  - Perspective 변경: 오른쪽 위 Open Perspective / Spring 선택해서 Open

#### 환경 설정: Window / Preference 에서 다음 설정

1. General / Workspace: 아래 오른쪽에 OTHER: UTF-8로 변경
2. HTML / CSS / JSP : UTF-8로 변경 (오른쪽 위에)
3. Server 설정
   - Runtime Environment
   - Apache Tomcat v9.0
   - Create a new local server
   - 톰캣 폴더 선택
4. Java Compiler 버전 변경 1.8로 변경



---



## 스프링 프로젝트 유형

> 스프링: 자바 기반 웹 프레임워크



### 스프링 웹 프로젝트

1. Spring Legacy Project
   - 스프링 템플릿 프로젝틀르 이용하는 프로젝트
2. Spring Starter Project
   - Spring Boot를 이용하는 프로젝트



### 1. Spring Legacy Project

- 스프링 템픞릿 프로젝트를 이용하는 프로젝트
- 모델2 방식 (MVC)의 프로젝트 생성 시 사용
- Spring MVC Project
- 서버 및 여러 설정 필요
- 실제 개발 업무에서 많이 사용하는 프로젝트



#### 2. Spring Starter Project

- Spring Boot를 이용한 프로젝트
- 최대한 간단하게 실행하고, 배포가 가능한 수준의 웹 어플리케이션을 제작하기 위한 목적
- 개발에 필요한 모든 환경 설정을 갖추면서 최소한의 개발을 해야하는 경우 사용
- 개발자가 복잡한 설정 없이 개발 환경이 준비되기 때문에 초보 개발자도 쉽게 웹 프로젝트 생성



#### c.f. 3. Simple Spring Maven (Maven Project)

- Spring 라이브러리의 기본 세트를 포함하는 Maven을 사용해서

  간단한 Spring 프로젝트 생성

##### 3.1. Maven (메이븐)

- Java 용 프로젝트 관리 도구
- XML 기반의 정적인 빌드 제공

##### 3.2 Gradle (그레이들)

- 그루비(Groovy) 스크립트 기반의 동적인 빌드 기능 제공
- 안드로이드 앱 만들 때 필요한 공식 빌드 시스템
- 메이븐 보다 빌드 작업이 간단
- 별도의 스크립트를 통해서 사용할 애플리케이션 버전, 라이브러리 등 설정 가능 



---



## 의존성 (Dependency)

> 객체 간의 의존성

- 한 클래스에서 다른 클래스의 객체를 통해 그 클래스의 메소드를 실행할 때

  "의존한다"라고 표현

- e.g. `xxxDAO dao;` `xxxDTO dto;`

- new 연산자를 통해 다른 클래스의 객체 생성해서 사용

  `BookDTO dto = new BookDTO();`



#### A 클래스에서 B 클래스의 객체를 생성해서 사용하는 경우

1. 지금까지 해왔던 개념

   - A 클래스에서 직접 생성
   - 일체형으로 묶여 있음
   - 강한 의존 관계

   ``` java
   class A {
       private B b;
       
       public A(){
           b = new B();	// B클래스의 객체 b 생성
       }
   }
   ```

2. 앞으로 사용할 개념 (DI)

   - 외부에서 만든 객체를 받아서 사용

     (조립된 부품을 받아서 사용하는 개념)

   ```java
   class A {
       private B b;
       
       public void setB(B b){	
           // setter메소드를 통해서 외부에서 넣어준다(아규먼트로 전달 injection)
           this.b = b;
       }
   }
   ```

   DI (Dependency Injection) 주입

   - 객체 간의 의존성을 개발자가 설정하는 것이 아니라
   - 스프링 컨테이너가 주입시켜주는 기능
   - 장점: 객체를 쉽게 확장하고 재사용할 수 있음
   - 외부에서 생성된 Bean(객체)를 IoC 컨테이너가 넣어주는 방식 (주입: injection)
   - 일반적으로 부품(Bean)을 조립 (의존성 주입)해서 사용한다는 개념



#### DI (의존성 주입) 방법을 사용하는 이유

- 의존하는 객체의 클래스가 변경되거나 다른 클래스의 객체를 사용하게 될 경우

  - 의존 관계에 있는 다른 모든 클래스의 소스 코드도 수정해야함

- 의존성 주입 방법을 사용하면, 클래스 결합 상태를 변경하거나 객체를 주입하는 부분만 수정하면 되므로

  수정할 코드의 양을 줄일 수 있다는 장점이 있음

- e.g. A1클래스를 사용하다가 A2 클래스로 변경할 경우

  - 설정 파일에서 클래스 이름만 변경해주면 됨

    ``` javascript
    <bean id="a" class="com.package.A1"> // 에서 A2로만 바꿔주면 됌
    ```

    

#### 스프링에서 의존성 주입 방법

1. XML을 이용한 방법
   - XML 설정 파일에 `<bean>` 설정
     - 생성자 기반 DI
     - Setter 기반 DI
2. Annotation을 이용한 방법
   - 자바 코드에서 '@어노테이션'으로 설정



---



#### 실습 

1. #### DI를 사용하지 않는 예제

   - Controller 클래스와 Service 클래스 사이에 의존성 존재
   - Controller 클래스에서 new 연산자 사용해서 Service 클래스에서 객체 생성해서 사용

- 프로젝트 생성
  - 도메인 이름 형식: com.company.app
  - Group id (도메인 이름):  com.di_project.ex
  - Artifact id (프로젝트 이름): di_01
- com.di.no_spring_no_di
  - nameService
  - nameController
  - nameMain



2. #### 생성자 기반 DI

   - 의존성이 있는 객체를 new를 통해 직접 생성하지 않고
   - 생성자를 통해 외부에서 전달 (주입: inject)
   - 아직 스프링의 DI는 아님

   - com.di.no_spring_di_constructor



3. ####  Setter 기반 DI

   - Setter 메소드를 사용해서 의존성 주입을 수행
   - com.di.no_spring_di_setter



---

### Spring DI

스프링의 의존선 주입: 스프링의 핵심 기능

- 스프링 프레임워크는 컨테이너 역할을 하기 때문에
- 스프링 컨테이너(IoC 컨테이너)라고도 함
- 스프링은 필요한 빈을 생성해서 컨테이너에 넣어 관리
- 필요한 곳에 주입해줌
- 빈을 생성하기 위해 설정과 의존 객체를 주입시키는 설정 필요



### 2가지 Spring DI

	##### 1) XML을 이용한 DI

- 별도의 설정파일(xml)을 사용해서 빈 생성, 객체 주입 설정
- 생성자 기반 DI
- Setter

##### 2) Annotation을 이용한 DI





### 1) XML을 이용한 DI

- XML 파일에 

  빈 (Bean: 부품)을 정의(생성)하고 

  `<bean id="빈 이름" class="패키지명.클래스명">`

- 의존성 설정 ( 부품을 조립: DI )

  `<ref bean="의존하는 빈">`

- XML을 이용해서 의존성을 주입하기 위해서는

  생성자 기반일 때는 생성자가 반드시 있어야 하고

  Setter 기반일 때는 Setter 메소드가 반드시 있어야 함



##### c.f. 스프링은 Pre-loading 방식 사용

- ApplicationContex를 이용해서 컨테이너를 구동하면
- 컨테이너가 구동되는 시점에 스프링 설정 파일에 등록된 빈을 생성하고 컨테이너에 로드



---



### 스프링 DI 실습

#### 1. XML을 이용한 DI: 생성자 기반

- 클래스에 생성자가 있어야 하고

- 스프링 설정 파일(xml)에서 빈을 정의할 때

  `<constructor-arg ref="의존하는 빈">`

- com.id_spring_di_xml_constructor



설정파일 생성: xml

src/main/resources 폴더에 Spring Bean Configuration File 선택하고

application-context.xml



#### NameMain 클래스에서 하는 역할

- 컨테이너 객체를 생성하고

  AbstractApplicationContext context = 

  new GenericXmlApplicationContext("application-context.xml");

  

  라이브러리 없어서 오류 -> pom.xml 파일에 라이브러리 추가

  

- 컨테이너에 컴포넌트 (빈) 가져옴

- pom.xml 파일에서 Dependendcies Add 안될 때

- Window / Preference

  - 왼쪽에서 Maven: 오른쪽에서 [Download repository index updates on startup 체크]
  - Apply and Close 창 닫고

- Window / Show View / Other

  - Maven: Maven Repositories 선택하고 open

- 오른쪽 아래에 창이 열리면

  - Gloval Repositories / central에 우클릭하고 Rebuild Index



---

#### Q. 연습문제

- 패키지: com.di_spring_di_xml_constructor_ex1
- 클래스 생성
  - Speaker 클래스
    - volumeUp(): 볼륨을 키웁니다
    - volumeDown(): 볼륨을 낮춥니다
  - TV 클래스
    - Speaker speaker;
    - volumeUp() / volumeDown()
    - TV 클래스에서 Speaker 클래스의 volumeUp() / VolumeDown()를 호출해서 볼륨 조정
  - TV Main 클래스에서
  - XML 기반으로 생성자를 통해  DI 구현
    - application-context2.xml



---



### 2) XML을 이용한 DI: Setter 기반

-  클래스에 반드시 Setter 메소드가 있어야 한다

- 생성자 사용 안함 (기본 생성자 외에 다른 생성자 없음)

- 스프링 설정 파일(XML)에서 `<property>` 태그를 이용해서 의존 객체 주입

  `<property name="nameService" ref="nameService">`

  - name: setter 메소드 이름 (setNameService())
  - ref: 참조 객체 이름 (참조하는 빈 이름)

   

- 예제
  - 패키지: com.di.spring_di_xml_setter



---

### 설정 파일에서 빈 생성하면서 값 초기화 (값 설정)

- 생성자 기반
- Setter 기반
- 패키지: com.di.spring_xml_value_constructor
- 패키지:com.di.spring_xml_value_setter

---

#### Q. 연습문제 3

- com.di.spring_xml_value_setter
- application-context7.xml
- Book 클래스
  - 설정 파일에서 빈 생성하면서 값 초기화
  - Setter 기반

---

### 설정 파일에서 빈 생성하면 값 초기화 (값 설정) - 의존성 주입

- com.di.spring_di_xml_value_constructor
- com.di.spring_di_xml_value_setter
  - application-context9.xml



---

---

## ***Annotation***을 이용한 DI

- xml 설정 파일에서 `<bean>` 태그를 이용해서 설정하였던 빈 설정을

  Annotation(메타 데이터)를 이용해서 자바 코드에서 설정

- e.g. XML 설정 파일에서 빈을 설정하지 않고 스프링이 자바 소스 코드를 읽어서

  클래스에 @Component 어노테이션이 붙은 클래스 객체화 (bean 설정)

  A1 클래스의 객체를 A2 클래스의 객체로 변경하려면 

  - A1 클래스에서 @Component를 제거하고
  - A2 클래스에 @Component를 붙이면 됨
  - @Autowired 어노테이션을 사용해서 bean 자동 삽입



- XML 설정 파일에 context 네임스페이스 추가

  - 빈 설정을 위한 어노테이션ㅇ르 사용하기 위해서는

    설정 파일에 context 네임스페이스가 추가되어 있어야 함

  - `<context:component-scan>` 태그 이용해서 빈으로 등록될 클래스 패키지 지정

  - 의미: 자바 소스 코드에서 @Component로 등록된 클래스를 찾아서(scan) 클래스를 객체화(빈 설정)



### ***Annotation***의 종류

- #### 빈 생성과 관련된 Annotation

  - `@Component`
    - `@Controller`
    - `@Service`
    - `@Repository`
  - `@Configuration`
    - `@Bean`

- #### DI 관련 Annotation

  - `@Autowired` / `@Inject`
  - `@Qualifer`
  - `@Resource`



### DI 관련 Annotation

- xml 설정 파일에 있는 `<bean>`에 대해 DI 하거나 자바 코드에서 생성도니 bean에 대해 DI 할 수 있음

- @Autowired: 타입을 기준으로 의존성 주입
  - 스프링 빈에 의존하는 다른 빈을 자동으로 주입할 때 사용
  - 스프링에서 지원
- `@Inject`: `@Autowired`와 동일 (자바에서 지원)
- `@Qualifer`: 특정 빈의 이름 지정
  - 동일한 Interface를 구현한 클래스가 여러 개 있는 경우
  - 사용하고자 하는 특정 빈의 이름을 지정할 때 사용
- `@Resource`: `@Autowired` 와 `@Qualifer` 를 같이 사용하는 것과 동일 (자바에서 지원)



### 프로젝트 새로 생성

- New / Maven 프로젝트 생성
  - Create a simple project 체크
  - Group Id (도메인 이름): com.di_project.ex
  - Aritifact Id (프로젝트 이름): di_02
  - pom.xml `<dependency>` 추가: di_01에서 복사

- 패키지 생성: com.spring_di_annotation
- 필요한 클래스
  - INameService (인터페이스)
  - NameService (클래스)
  - NameController (클래스)
  - NameMain (클래스)
- 설정 파일: application-context.xml
  - Annotation을 사용하기 위해서는 context 네임스페이스 추가
    - application-context.xml 생성한 후에 아랫쪽에 Namespaces 탭 선택
    - context 체크 
  - 빈 생성

1. `@Autowired`: 스프링 빈에 의존하는 다른 빈을 자동으로 주입할 때 사용

2. `@Qualifer`: 특정 빈의 이름 지정 (동일한 Interface를 구현한 클래스가 여러 개 있는 경우)
3.  `@Resource`: `@Autowired` 와 `@Qualifer` 를 같이 사용하는 것과 동일 (자바에서 지원)



#### `@Autowired`의 위치

- 클래스 선언부
  - 기본 생성자를 호출하면서 injection이 이루어짐
- Setter 메소드 위에
  - Setter 메소드 호출하면서 injection이 이루어짐



---



### 빈 생성과 관련된 Annotation

- `@Component`
  - `@Controller`
  - `@Service`
  - `@Repository`
- `@Configuration`
  - `@Bean



#### 빈 생성 어노테이션

- 빈 생성 (설정)을 위해 클래스 위에 추가되는 어노테이션

- 클래스 이름 위에 붙이면 해당 클래스 파일에 대한 bean 자동 생성

- (xml 파일에서 bean 생성하지 않음)

- bean의 이름은 클래스 이름에서 첫 문자 소문자

  e.g. NameService 클래스의 Bean 이름은 nameService



#### 어노테이션을 사용하기 위해 xml 설정 파일에서 필요한 작업

- xml 설정 파일에 context 네임 스페이스 추가 필요

  `<context:component-scan base-package="패키지명"/>`

- @Component 어노테이션이 적용된 클래스를 빈으로 등록



### `@Component` 어노테이션

- 클래스를 빈으로 등록합니다 (부품 등록)
- 빈 id를 지정할 수 있음
- `@Component`("빈 이름") == `<bean id="빈 이름">`에 해당



- 패키지: com.spring_di_annotation_component
- 사용 클래스
  - INameService 인터페이스 : 변경 없이 그대로 사용
  - NameService 클래스: 빈 생성
    - `@Component` 어노테이션 추가
  - NameController 클래스: 빈 생성
    - `@Component` 어노테이션 추가
    - 생성자 삭제
    - NameService 객체 사용
  - NameMain 클래스: xml 파일명만 변경
    - NameController 클래스 사용



#### @Component 어노테이션의 의미론적 어노테이션

- @Component: 일반적인 컴포넌트

  - 특화된 @Component 어노테이션

    - 클래스의 역할에 따라 의미론적으로 구분

      - @Controller 컴포넌트: 컨트롤러 클래스에 사용

      - @Service 컴포넌트: 서비스 클래스에 사용

      - @Repository 컴포넌트: DAO 클래스 또는 Repository 클래스에 사용

        

  Bean named 'nameController' is expected to be of type 'com.spring_di_annotation_component2.NameController' but was actually of type 'com.spring_di_annotation_component.NameController'