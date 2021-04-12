# JSP ***(Java Server Page)***

> #### Java 기반으로 HTML 문서 내에서 Java코드를 삽입해서 
>
> #### 웹 서버에서 동적으로 웹 페이지를 생성해서 
>
> #### 클라이언트(웹 브라우저)에게 반환해주는
>
> #### 서버 사이드 스크립트 언어

- JSP를 통해 HTML과 동적으로 생성된 컨텐츠를 혼합해서 사용 가능
- Servlet을 보완한 스크립트 방식 표준
- Servlet 기능 + 추가 기능
- JSP는 실행되면서 Servlet(.java) 으로 변환되어 컴파일돼서 .class 파일로 만들어져서 실행
- View를 담당하는 페이지로 사용



### JSP 와 Servlet 의 차이점

- JSP: HTML 내부에 Java 소스 코드가 들어 있는 형식 (사용하기 편리)
- Servlet: Java 코드 내에 HTML 코드가 있어서 읽고 쓰기가 불편



### JSP 페이지 구조

- 정적 페이지 + 동적 페이지  = JSP

- 동적 페이지 구현

  - #### <%@ %>

  - #### <% %>

  - #### <%! %>

  - #### <%= %>



### JSP 인코딩 설정



### JSP 태그 

- `<%`로 시작하고 `%>`로 종료
- @, !, -, -- 문자를 추가하여 태그의 의미 부여



#### 구분					태그 표기법				         설명

지시어							`<%@	%>`						JSP 페이지 속성지정

선언부							`<%!	%>`						변수 선언 및 메소드 정의

표현식							`<%=	%>`						계산식, 함수 호출 결과, 변수 값 등 출력

스크립트 릿		    		`<%	%>`						자바 코드 기술 (자유롭게 기술)

주석		    				`<%-- --%>`					JSP 페이지 주석

액션 태그					`<jsp:액션>`					자바 빈, include / forward  / param등



| 구분 | 태그 표기법 | 설명 |
| ---- | ----------- | ---- |
|      |             |      |



### JSP 페이지 기본 구성 요소

- JSP 페이지 내용: HTML 문서 내용(태그 / 내용) 	/ 	JSP 태그 	/ 	자바 코드



### JSP 페이지 구성

- 지시어
  - `page`, `include`, `taglib`
- 스크립트 요소
  - 선언문  /  표현식  /  스크립트릿
- 액션 태그



### 지시어 

> JSP 페이지의 전체적인 속성을 지정할 때 사용

- JSP 컨테이너에게 전달하는 JSP 페이지 관련 메시지

  `<%@ 지시어 속성1=값1, 속성2=값2, ..., %>`

- `page`, `include`, `taglib`

- JSP 페이지에 대한 속성 설정

  `<%@ page language="java"` 

  `contentType="text/html; charset=UTF-8"`

  ` pageEncoding="UTF-8"%>`



#### `include` 지시어

​	`<%@ include file="포함될 파일의 url" %>`

- 공통적으로 포함될 내용을 가진 파일을 해당  JSP 페이지 내에 삽입하는 기능을 제공



### 변수는 "선언부" ,  "스크립트릿"영역에서 자유롭게 선언 가능

### 메소드는 "선언부"에서만 선언이 가능



### JSP 내장 객체

- 클라이언트에서 웹 서버에 JSP 페이지를 요청하면 자동으로 생성
- 객체를 별로도 생성하는 과정없이 바로 사용 가능



####  내장 객체 종류

- 입 / 출력: `request` / `response` / `out`
- 서블릿: `page` / `config`
- 컨텍스트: `session` / `application` / `pageContext`
- 예외처리: `exception`



#### request 객체

- 사용자의 요청을 받을 때 사용하는 객체
- getParameter(): 1개의 값을 받을 때
- getParameterValues(): 동일한 이름으로 여러 개의 값을 받을 때 (배열로 받음)
- getParameterNames(): name 속성 모를 때 사용



#### response 객체

- 서버로부터 사용자에게 응답할 때 사용하는 객체
- JSP 처리 결과를 웹 브라우저에 전송
- addCookie(): 쿠키 설정
- setContentType(): 페이지의 content type (tex / html) 설정
- sendRedirect(): 페이지 이동 (페이지 포워딩)



#### ou 객체

- 웹 서버에서 웹 브라우저에게 출력 스트림으로 응답할 때 사용
- out.println("출력 문자열");



### 서버에서 전송되는 데이터 타입

- 클라이언트에 폼을 통해 전송되는 데이터는 문자열
- 숫자 연산을 할 경우 숫자형을 형변환 필요





### JSP 제어문

- if문

- for문

- while문



#### for문 연습문제

- forForm.jsp: 구구단 입력: 7
- forResult.jsp 에서 입력 받은 단 출력
  - 테이블 한 행씩 출력



---

### 액션태그

> JSP 페이지 내에서 어떤 동작을 지시하는 태그
>
> 어떤 동작(액션)이 일어나는 시점에서 페이지와 페이지 사이에서 제어 이동 기능을 제공하거나
>
> 다른 페이지의 실행 결과를 현재 페이지레 포함하는 기능 제공



#### 액션 태그의 종류

- `include`
- `forward`
- `useBean`
- `setProperty`
- `getProperty`
- `plug-in`



#### `include` 액션 태그: `<jsp.include>`

- 다른 페이지의 실행 결과를 현재 페이지에 포함시킬 때 사용



#### `forward` 액션 태그: `<jsp:forward>`

- 현재 웹 페이지에서 다른 특정 페이지로 전환
- 웹 페이지 간의 제어를 이동할 때 사용



#### `param` 액션 태그: `<jsp:param>`

- 이동하는 페이지에 파라미터 값ㅇ르 전달할 때 사용



#### `useBean` 액션 태그: `<jsp.useBean>`

- 자바빈을 JSP 페이지로 사용할 때



#### `setProperty` 액션 태그: `<jsp.serProperty>`

- 프로퍼티 값을 설정할 때 사용



#### `getProperty` 액션 태그: `<jsp.getProperty>`

- 프로퍼티의 값을 얻어낼 때 사용

- 페이지를 모듈화할 때 사용
- include 지시어와의 차이점





| 구분        | `<jsp:include>` 액션 태그                                    | `include` 지시어                                     |
| ----------- | ------------------------------------------------------------ | ---------------------------------------------------- |
| 형식        | `<jsp:include page=""/>`                                     | `<%@ include file="" %>`                             |
| 처리 시점   | 실행 시                                                      | 자바 소스로 변환 시                                  |
| 기능        | 별도의 파일로 처리<br />제어권이 이동했다가 다시 돌아옴      | 현재 파일에 삽입 (합쳐서 하나의 java 파일 생성)      |
| 데이터 구성 | 동적 데이터로 구성                                           | 정적 데이터로 구성                                   |
| 용도        | 화면 레이아웃 모듈화 할 때<br />(top / bottom 페이지 포함시킬 때) | 여러 페이지에서 사용하는 변수를 지정하고 포함시킬 때 |



### 처리 시점 확인 



#### include 지시어 

include1.jsp	←	include2.jsp

​		↓

include1.java

​		↓

include1.class



- include2.jsp 가 변경되면
- include1.jsp 다시 컴파일 (낭비)
- 따라서 자주 변경되지 않는 정적 데이터로 구성



#### `<jsp:include>` 액션 태그

include1.jsp				include2.jsp

​		↓									↓

include1.java	  		include2.java

​		↓								    ↓

include1.class	↔	include2.class



- include2.jsp 변경되면
- include2.jsp만 다시 컴파일
- 동적인 데이터로 구성

---

### `<jsp:param>`

- forward 및 include 액션 태그에서 데이터를 전달하기 위해 사용
- name 과 value로 구성
- `<jsp:param name="id" value="abcd" />`
- param 액션 태그로 전당되는 값을 받을 때
- request.getParameter("id")

---



### 자바 빈 ***(JavaBeans)***

> DTO / VO 와 같은 개념
>
> 데이터를 다루기 위해 자바로 작성되는 소프트웨어 컴포넌트로 재사용 가능

- 입력 포므이 데이터와 데이터베이스의 데이터 처리 부분에서 활용
- 클래스로 만들어짐
  - 멤버 필드로 속성(property)이 있고
  - 멤버 메소드로 Getter / Setter 메소드 포함
  - setXxxx(): 프로퍼티에 값 저장
  - getXxxx(): 프로퍼티 값 반환
- 액션 태그를 이용해서 Bean 사용
- 속성 접근 제어자: private
- Getters / Setters: public



### 자바 빈 관련 액션 태그

- `useBean` 액션 태그: `<jsp:useBean>`
  - 자바 빈을 JSP 페이지에서 사용할 때 사용
  -  `<jsp:useBean id="자바빈 이름" class="패키지명을 포함한 클래스명" scope="" />`
- `setProperty` 액션 태그: `<jsp:serProperty>`
  - 프로퍼티의 값을 설정할 때 사용 (데이터 설정)
- `getProperty` 액션 태그: `<jsp:getProperty>`
  - 프로퍼티의 값을 얻어낼 때 사용



#### scope: 자바 빈의 유효 범위

- page / request / session / application



