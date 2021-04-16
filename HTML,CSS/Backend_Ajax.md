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

