## ***MyBatis***(마이바티스)

> #### ***ORM(Object Relation Mapping***, 객체 관계 맵핑***)*** 프레임워크

- 자바에서 JDBC를 이용해서 데이터베이스 연동할 때

  Java 언어와 sql 언어가 한 파일에 존재하면서 재사용성이 좋지 않음

- MyBatis는 JDBC의 이런 단점을 개선해서 sql 명령어를 별도로 xml 파일로 분리해서

  sql 명령어와 자바 객체를 맵핑해준 기능을 제공

- sql 명령어 재사용 가능



##### ***MyBatis*** 특징: SQL 명령어를 자바 코드에서 분리해서 XML 파일에서 관리



#### JDBC를 사용할 경우

- ##### Controller → IService / Service → IDAO(선택) / DAO (SQL 문장) → DB

#### MyBatis를 사용할 경우

- ##### Controller → IService / Service → IDAO(필수) / mapper.xml(sql 문장) (DAO 대신 mapper.xml 사용)



### 스프링에서 MyBatis 사용하기 위한 설정

1. 프로젝트 생성
2. pom.xml에서 의존성 설정
   - 프로젝트 의존성
   - 데이터베이스 의존성 
     - (Spring JDBC 의존성 / Connection Pool 의존성 / Oracle JDBC Driver 의존성)
   - MyBatis 의존성
3. web.xml 인코딩 필터 추가
4. 프로퍼티 파일 작성: jdbc.properties
5. 스프링 설정 파일: application-config.xml
   - DataSource / Mapper 지정
6. web.xml: 스프링 설정 파일 지정
7. 클래스 구성 (CRUD, sele**c**t/inse**r**t/**u**pdate/**d**elete)
   - Controller
   - IService / Service
   - VO
   - IDAO / mapper.xml
   - View 페이지(.jsp) - select / insert / update / delete / index



#### 데이터 베이스 작업

- 관리자: 사용자 생성: SPRING
- 새 접속: SPRING실습
- 사용자: SPRING
- 비밀번호: 1234
- 테이블 생성: product



New / Spring MVC Project

프로젝트 이름: spring_mvc_mybatis

패키지 이름: com.spring_mvc.project (.project 가 ContextPath가 된다 / 8080  다음에 나옴)



1. pom.xml 버전 변경

   - 기본 환경 확인
     - Spring Framework 3.1.1 
     - Java version 1.6
     - Maven compiler
       - source 1.6
       - target 1.6
   - 변경할 버전
     - Spring Framework 4.3.4 (ln.12)
     - Java version 1.8 (ln.11)
     - Maven compiler
       - source 1.8 (ln.141)
       - target 1.8 (ln.142)

   

2. 프로젝트 설정 변경 (프로젝트 이름 우클릭)

   - Java Compiler: 1.8 버전으로 변경

   - Java Build Path: JRE 수정 (Default 1.8.0 으로)

   - Project Facets: Java 버전 변경 (1.8 버전으로)

     ​						   Dynamic Web module 버전 변경 (3.0)

   

3. Maven / Update Project (데이터베이스 와 마이바티스 설정 끝난 후에)

   - 프로젝트 이름 우클릭 Maven → Update Project

---

##### ojdbc-6.jar

C:\oraclexe\app\oracle\product\11.2.0\server\jdbc\lib 에 들어있는 ojdbc6.jar 파일을 아래 폴더에 복사

C:\Users\rangs\.m2\repository\com\oracle\ojdbc\6 폴더에 저장 (폴더 없으면 새로 생성)

파일명을 ojdbc-6.jar로 변경

##### 데이터베이스 의존성 

- (Spring JDBC 의존성 / Connection Pool 의존성 / Oracle JDBC Driver 의존성)
- txt파일 pom.xml 에 붙여넣기(ln.35)

##### MyBatis 의존성

##### web.xml 인코딩 필터 추가 (한글깨짐방지)

##### 프로퍼티 파일 작성: jdbc.properties

- 위치: src/main/resources에 database 폴더 만들고 jdbc.properties 파일 생성
- 데이터베이스 연결 정보 설정
  - 프로퍼티 파일에 작성해놓음
  - 이 파일 안만들고 설정 파일 안에 직접 넣어도 됨
  - 프로퍼티 파일을 만들어서 사용하는 이유: 보안 때문
    - DB 연결 정보는 내용이 변경될 수 있으므로 외부 .properties 파일로 작성해서 별도로 관리
    - git 저장소에 DB 접속 정보가 노출되지 않도록 하기 위함

##### 스프링 설정 파일: application-config.xml

- DataSource / Mapper 지정
- 위치: src/main/resources에 spring 폴더 만들고 application-config.xml 파일 생성

##### web.xml: 스프링 설정 파일 지정

##### 클래스 구성 (CRUD, sele'**c**'t/inse'**r**'t/''**u**'pdate/'**d**'elete)

- Controller
- IService / Service
- VO
- IDAO / mapper.xml
- View 페이지(.jsp) - select / insert / update / delete / index

---

#### 패키지 생성

- controller: ProductController 클래스		@Controller	/ @Autowired

- dao: IProductDAO (인터페이스)

  ​		 ProductMapper.xml

- model: ProductVO

- service: IProductService 인터페이스         @Service

  ​			  ProductService 클래스

---

##### ProductMapper.xml

- https://mybatis.org/mybatis-3/getting-started.html 에서 복사

  ``` xml
  <!DOCTYPE mapper
    PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  ```

---

##### 사용자 요청 (전체 상품 조회) → Controller → Service → IDAO/Mapper.xml

#####                    사용자				   ←                     ←                ←



---

#### Q. 연습문제

- 새 프로젝트 생성

- 도서 관리 프로젝트 작성
- 테이블: 새로 작성 또는 기존 테이블 사용



프로젝트 명: spring_mvc_mybatis_book

패키지 명: com.spring_mybatis.book	(.book이 ContextPath)

도서 관리 프로그램 작성

- 전체 도서 정보 조회
- 도서 상세 정보 조회
- 도서 정보 등록
- 도서 정보 수정
- 도서 정보 삭제

