## ***Ajax(Asynchronous JavaScript and XML)***

> 클라이언트에서 비동기 방식으로 자바스크립트를 이용해서 
>
> 화면 전환 없이 서버 측에 데이터를 요청할 때 사용

- HTML, XML, JSON, text 등의 다양한 데이터 처리 가능
- 웹 서버 환경에서 실행



#### 형식: JQuery 형식 (jQuery 파일이 있어야 함)

``` javascript
$.ajax({
	url: "전송되는 페이지 (~로 전송)",
    type: "데이터 전송 방식 (get/post)",
    date: "전송할 데이터",
    dataType: "요청하는 데이터 타입(html, xml, json)",
    success: function(data, textStatus){	//  결과를 받을 매개변수 사용
        // 전송 및 요청 성공시 실행 부분
    },
    error: function(date, testStatus){
        // 오류 발생 시 실행 부분
    },
    complete: function(){
        // 완료 시 실행 부분
    }
});
```



#### `$.ajax()` 메소드

- 사용자가 지정한 URL 경로에 있는 파일의 데이터를 전송하고 

  입력한 URL 경로의 파일로부터 요청한 데이터를 불러오는데 사용

  불러올 수 있는 외부 데이터는 텍스트, HTML, XML, JSON 유형 등

#### `serialize()`: 

- 폼에 입력된 값을 쿼리 스트링 방식의 데이터로 변환하여

  액션 페이지에 전송

- 예: `id=abcd&pawd=1234&&name=kim,...'`

---

##### Q. 과제1

- html/JavaScript: 입력한 값 출력하기( alert() 사용)

##### Q. 과제2

- Ajax() 사용해서 서버로 보내고 

  (가정: DB에서 다 처리했다고 가정하고)

  보낸 값을 다시 클라이어언트로 보내서 alert() 출력

---

#### CDATA: Unpared Character Data

- 파싱되지 않는 문자 데이터

- SQL 쿼리 작성할 때 <, >, &, || 등을 사용해야 하는 경우

- XML 에서 태그로 인식해서 오류가 발생

- XML에서 XML 파싱 대상이 아니고 단순 문자열로 처리하라는 의미

  ``` sql
  <![CDATA[
      SELECT * FROM product WHERE prdPrice > 10000; 
      									/* '>'가 태그로 인식되는 것 방지
  ]]>
  ```

  

---

### ***Spring REST API***



#### ***REST***

- 브라우저에서 페이지 요청 시

- PC에서는 페이지 전체를 다시 전송해서 표시해도 문제 없지만

  스마트폰 등의 모바일 기기에서는 기존 화면은 그대로 유지하면서 

  필요한 내용만 추가해서 화면에 표시

- 모바일기기가 유선기기보다 네트워크 전송량이 떨어지므로

  현재 화면은 그대로 유지하면서 필요한 데이터만 전송받아서 빠르게 표시하기 위해서

- 대표적인 경우: Ajax 이용

- 따라서 데이터만 전송하는 기능 표준화 필요성이 대두되면 REST 방식이 대안으로 사용됨



### REST ***(Representation State Transfer)***

> URI가 고유한 리소스를 처리하는 공통 방식

- 세션 정보나 쿠키 정보를 별도 저장하고 관리하지 않고 API 서버는 들어오는 요철만 단순 처리
- REST API 설계기준
  - URI 정보의 자원 표현
  - 자원에 대한 행위 HTTP (GET, POST, PUT, DELETE)로 표현



#### REST API 중심 규칙

- URI는 정보의 자원을 표현해야 한다

- 자원 표현

  ` GET /members/1`

  `DELETE /mebers/2`

  `POST /members/3`

- 슬래시 구분자는 계층 관계를 나타내는 데 사용

- 마지막에는 슬래시 (/) 포함하지 않음

- URI 소문자로 사용

- 파일 확장자는 URI에 포함하지 않음



##### REST 방식으로 제공되는 API를 REST API (또는 RESTful API)라고 함

- 트위터와 같은 Open API에서 많이 사용
- 전송 방식을 나타내는 메소드 속성의 값에 따라 리소스에 대한 추가 작업 요청



#### 스프링에서의 REST 방식의 데이터 처리

- 스프링 3버전: `@ResponseBody` 어노테이션 지원
- 스프링 4버전: `@RestController` 어노테이션



##### `@RestController` 이용해 REST 기능 구현

- 컨트롤러에게 브라우저로 기본형 데이터, VO 객체의 속성 값, Map에 저장된 데이터 전송
- 서버 → 클라이언트 데이터 전송



##### `@Controller` vs `@RestController`

- `@Controller`: 결과를 jsp(view)로 표시
- `@RestController`: 별도의 view를 제공하지 않은 채 데이터 전달



---

#### `@RestController` 사용해서 클라이언트로 문자열 전송



프로젝트 생성: Spring MVC Project

프로젝트명: spring_mvc_rest

패키지명: com.spring_mvc.rest



---

- servlet-context.xml 설정 파일에서

  컨트롤러 없이 index 페이지 설정하는 방법

<mvc:view-controller path="/" view-name="index"/>

---



#### `@RestController`를 이용해서 VO 객체 전달

- VO 객체의 속성 정보를 JSON 형식으로 전달

- pom.xml에 JSON 의존성 추가

  ``` xml
      <!-- JSON  --> 
      <dependency>
          <groupId>com.fasterxml.jackson.core</groupId>
          <artifactId>jackson-databind</artifactId>
          <version>2.5.4</version>
      </dependency>
  ```

  

---

#### `@RestController`를 이용해서 컬렉션 객체 전달

- List를 JSON으로 만들어서 전송
- /memberList

---

#### `@RestController`를 이용해서 Map 전달

- Map에 저장된 데이터 전송

---

##### `@PathVariable`을 사용하면 브라우저에서 요청 URL로 전달된 매개변수 값을 가져올 수 있다

---

#### `@RequestBody`와 `@ResponseBody` 사용하기

- 실제 REST는 Ajax 기능과 연동해서 자주 사용
- 브라우저에서 JSON 데이터를 컨트롤러 전송될 때 컨드롤러에서 JSON 객체로 변환하는 기능 구현



##### `@RequestBody`: 브라우저에서 전달되는 JSON 데이터를 객체로 자동 변환 (클라이언트→서버)

##### `@ResponseBody`: 브라우저에게 JSP가 아닌 텍스트나 JSON으로 결과 전송 (서버→클라이언트)

	- `@Controller` 클래스에서 사용



#### 리소스 파일 (image, css, js) 경로 설정

- servlet-context.xml

  ``` xml
  <mvc:resources location="/resources/" mapping="/**"/>
  <mvc:resources location="/resources/js/" mapping="js/**"/>
  ```

- src/main/webapp/resources 폴더

---

views에 JSONTest.jsp

---

#### FrontEnd 프로젝트: HTML, JS, CSS, image 파일을 스프링 프로젝트로 옮김

- JS, CSS, image 파일: 리소스 파일
  - 위치: src/main/webapp/resources 폴더에 위치 
  - 설정 파일 (servlet-context.xml)에서 리소스 경로 지정
- index.jsp에 index.html 내용 복사
  - index.jsp / top.jsp / bottom.jsp 로 분리
- 지금 만든 index.jsp 이름 변경 → index01.jsp
- 새로 보내주는 index.jsp로 사용 (경로를 jstl 사용)



- views 폴더 안에 jsp 폴더 생성
  - jsp - top.jsp / bottom.jsp
- index.jsp에서 잘라오기
  - top.jsp: 첫줄 ~`</nav>` 잘라서 붙여넣기
    - `<body>` `<html>`
    - `<div id="wrap"` 삭제
  - bottom.jsp: `<footer>` ~ `</footer>` 잘라서 `<body>` 안에 붙여 넣기

---

##### 로그인 기능 구현

- 회원 클래스 파일 필요
  - MemberVO
  - IMemberService
  - MemberService
  - IMemberDAO
  - MemberController
  - MemberMapper.xml
- 로그인 폼 이동
- 로그인 체크
  - id와 pw 일치하면 세션 변수로 저장
  - 세션 변수 값에 따라 top 메뉴 항목이 다르게 출력
  - 로그인 전: 로그인 회원가입
  - 로그인 후: ~ 님 환영합니다 로그아웃 게시판 장바구니 MyPage



---

##### 아이디 중복 체크

- pom.xml에 JSON 의존성 추가
- 회원가입 폼으로 이동
- id 중복 체크: ajax() 사용



---

## 스프링 부트 (Spring Boot)

> 스프링 프레임워크를 사용하는 프로젝트를 아주 간편하게 설정할 수 있는
>
> 스프링 프레임 워크 서브 프로젝트

- 톰캣 설치 등 여러 가지 복잡한 설정 필요 없음
- XML 기반 설정 과정 없이 프로젝트를 시작할 수 잇음
- Maven의 pom.xml 파일에 의존성 라이브러리의 버전을 일일이 저장하지 않아도 됨 
  - 스프링 부트가 권장 버전 관리
- 단독 실행되는 스프링 애플리케이션 구현 가능
- 톰캣 등 환경 구축에 필요한 서버 외적인 툴이 내장되어 있어서 별도 설치 필요 없음
- 스프링 부트 전용 STS
- JSP 뷰가 기본이 아니기 때문에 JSP 뷰를 사용할 경우
  - application.properties 파일에 설정 추가
  - pom.xml에 의존성 추가
  - src/main/webapp폴더에 WEB-INF 폴더와 views 폴더 추가

- application.properties 파일이 web.xml 대신하는 설정 파일
- main()  메소드 포함: 스프링 부트 프로젝트는 main() 메소드를 시작점으로 실행
- main() 이 반드시 있어야 함
- 이유: 스프링 부트의 웹 애플리케이션을 일반 자바 어플리케이션처럼 개발하려는 의도 때문



### 스프링 부트 프로젝트 생성

- New / Spring Starter Project
- JDBC API
- Oracle Driver
- Spring Web



- 오라클 의존성을 선택했으므로 데이터베이스 연결 정보 필요
- application.properties 파일에 DB 연결 정보 지정
- application.properties : web.xml 대신 설정 파일로 사용
- JSP 뷰가 기본이 아니기 때문에 JSP 뷰를 사용할 경우
  - application.properties 파일에 설정 추가
  - pom.xml에 의존성 추가
  - src/main/webapp폴더에 WEB-INF 폴더와 views 폴더 추가



##### 스프링 부트 프로젝트에서 자동으로 생성되는 클래스

1.

``` javascript
@SpringBootApplication
public class Myboot01Application {

	public static void main(String[] args) {
		SpringApplication.run(Myboot01Application.class, args);
	}

}
```

- `@SpringBootApplication`: 스프링 부트 애플리케이션으로 설정하는 어노테이션
- `main()`메소드
  - 스프링 생성시 자동으로 생성
  - 스프링 프로젝트는 반드시 main()이 있어야 함

2.

``` javascript
public class ServletInitializer extends SpringBootServletInitializer {

	@Override
	protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
		return application.sources(Myboot01Application.class);
	}

}

```

- `SpringBootServletInitializer`
  - 스프링 부트 애플리케이션을 web.xml없이 톰캣에서 실행하게 해주는 것
  - 그래서 스프링부트에는 web.xml과 context.xml 설정 파일이 없음



---

---



세미 프로젝트

- Spring Legacy Project: Spring MVC Project
- 쇼핑몰 기반
- 필수 기능 구현
  - 로그인
  - 회원가입
  - 전체 목록 출력 (e.g. 상품, 책, 옷, 등)
- 최종 제출
  - 프로젝트 계획서 (~ 수요일 오전 중 (11시 50분까지))
  - 포트폴리오
  - 프로젝트 압축 파일

- 발표: 4월 23일 오후 3시



get 방식: http://localhost:8080/test01 을 쳐서 들어가는 것

- doGet() 메소드 가 있어야 오류가 안난다

서블릿의 장점

서블릿은 클래스 상속 받아서 사용

서블릿 맵핑의 이유

쿠키, 세션에 대한 의미

setter 메소드가 있어야 한다 setter 기반 일 때는 



---

과제2 - 스프링 프로젝트로 작성

- ajax는 당연히 써야함

- LoginController

  - @RequestMapping("/xxxYyy") 
  - @RequestParam("id") String id 나 String id = request.getParameter("id"); 둘 중 하나 쓰기

- Ajax(): post

  - 데이터: 클라이언트 >>> 서버

    ​							 	 <<<

