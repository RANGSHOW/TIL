#### 실습 - 스프링 부트 프로젝트 생성

1. Tymeleaf방식 - 과제에서 사용한 방식

   - 의존성 설정

     ``` xml <dependency>
     <dependency>
     	<groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-thymeleaf</artifactId>
     </dependency>
     ```

     

   - html 파일 위치: src/main/resources 아래 templets 
   - 리소스 파일 (image/css/js): src/main/resources 아래 static

2. JSP 뷰 사용

   - JDBC API

   - Oracle Driver

   - Spring Web

   - 오라클 의존성을 선택했으므로 데이터베이스 연결 정보 필요

   - application.properties 파일에 DB 연경 정보 지정

   - application.properties: web.xml 대신 설정 파일로 사용

   - JSP 뷰가 기본이 아니기 때문에 JSP 뷰를 사용할 겨웅

     - application.properties 파일에 설정 추가
     - pom.xml에 의존성 추가
     - src/main/webapp 폴더에 WEB-INF 폴더와 views 폴더 추가

   - 자동 생성된 2개 클래스 

     - BootJspApplication.java

     ``` java
     @SpringBootApplication
     public class BootJspApplication {
     
     	public static void main(String[] args) {
     		SpringApplication.run(BootJspApplication.class, args);
     	}
     
     }
     // 스프링 프로젝트는 반드시 main()이 있어야 함
     
     ```

     - ServletInitializer.java

       ``` java
       public class ServletInitializer extends SpringBootServletInitializer {
       
       	@Override
       	protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
       		return application.sources(BootJspApplication.class);
       	}
       
       }
       // 스프링 부트 애플리케이션을 web.xml 없이 톰캣에서 실행하게 해주는 역할
       ```

       

---

#### 스프링 부트 프로젝트 생성 - MyBatis 사용

1. 스프링 부트 프로젝트 생성

   1) 프로젝트명: bootMybatis

   - Group: com.multi
   - 패키지명: com.multi.bootMybatis

   2) Dependencies 선택

   - SQL: JDBC API / Oracle Driver / MyBatis Framework
   - Web: Spring Web

   3) 프로젝트 생성 후 확인

   - pom.xml 내용 확인
   - Oracle 확인: ojdbc8로 자동 설정되어 있음
   - 자동 생성된 클래스 

   

2. 스프링 설정 파일: application-properties 파일 생성되어 있음

   1) application-propertiesdp 추가

   - 포트 번호
   - 데이터베이스 연결정보
   - JSP 뷰 설정
   - Mapper 위치 지정 

   2) JSP 뷰 페이지 설정 

   - pom.xml에 의존성 설정 추가

   - src/main/webapp 폴더에 WEB-INF/views 폴더 추가
   - index.jsp 생성
   - TestController에서 index.jsp 뷰 페이지로 설정하고 실행 확인

   

3. DB 연동 기능 구현

   1) 패키지 생성: com.multi.product

   - 앞에서 했던 product 클래스 모두 복사
     - ProductVO / IProductDAO / IProductService / ProductService / ProductController
     - 모든 view 페이지 복사: product 폴더에 모든 jsp 파일 복사

   2) mapper 파일 위치할 폴더 생성

   - src/main/resources 안에 mappers/product 폴더 생성하고 ProductMapper.xml 추가

   3) BootMybatisApplication 클래스에 추가

   - @ComponentScan(Product 컨트롤러 클래스 지정)
   - @MapperScan(IProductDAO 클래스)

   4) index.jsp에 링크 추가

   5) 실행: 이전에 했던 DB 처리 작업 CRUD 다 실행 

   

---

#### Q. 도서 관리 프로그램 작성

- 스프링 부트 프로젝트
- Oracle / MyBatis
- CRUD 기능 구현

---

## 형상 관리 (버전 관리)

팀프로젝트 진행하면서

- 프로젝트 변경 사항이 있으면 팀원이 같이 공유하도록 최신 버전으로 항상 유지
- 개발자가 수동으로 버전 관리를 하게 되면 
- 거의 대부분 개발 마지막에 통합해서 테스트가 진행되는 경우 발생
- 개발 도중 품질관리가 전혀 이루어지지 않기 때문에 개발 후반에 많은 문제 발생



### CI / CD

> 버전 관리는 자동으로 지속적으로 수행한다는 의미

- CI(Continuous Intergration): 지속적 통합 (통합 자동화)
  - 코드에 대한 통합을 지속적으로 진행함으로써 품질을 향상시키고 유지하려는 의도
- CD(Continuous Deploy 또는 Delivery): 지속적 배포 (배포 자동화)
  - 소프트웨어가 향상 신뢰 가능한 수준에서 배포될 수 있도록 지속적으로 관리한다는 개념



### CI 시스템 구축

- CI 서버가 Repository Server(Git 등)에 Commit 된 소스코드를 

  주기적으로 풀링해서 컴파일, 단위 테스트, 검사 등 과정 수행

- 신규 또는 업데이트된 소스코드의 결함 여부를 지속적으로 검증

- 검증 결과를 개발자에게 전달하고 결함 해결



### CI 구성 요소

- CI 서버: 빌드 프로세스 관리 서버: Jenkins, Travis CI, 등
- Repository Server: 각 개발자의 프로젝트 버전 관리: Git
- Build Tool: 소스코드 컴파일해서 실행 가능한 파일로 만드는 과정: Maven, Gradle, ...
- Test Tool: 작성된 코드로 자동으로 테스트 수행하는 도구: Junit, Mocha 등



### DevOps (데브옵스)

> 소프트웨어의 개발 (Development)과 운영(Operation)의 합성어

- 사람, 프로세스, 기술 등 합집합
- 소프트웨어 개발자와 정보기술 전문가간의 소통, 협업 및 통합을 강조하는 개발환경 또는 문화가 데브옵스
- 소프트웨어 개발 조직과 운영 조직 같의 상호 의존 및 협력 관계



### DevOps의 목적

- 소프트웨어 제품과 서비스를 빠른 시간에 개발 및 배포
- 운영 프로세스의 예측 가능성, 효율성, 보안, 유지보수 가능성 등을 극대화
- 자동화: 통합 자동화 / 배포 자동화



### DevOps의 이점

- 제품 생산 프로세스 전 과정을 자동화함으로써 제품을 더 빨리 빌드하여 고객 만족을 높여 성과 달성
- 출식 시간 단축
- 시장과 경쟁 지형에 따른 유연한 대응 가능
- 시스템 안정성 및 신뢰성 유지
- 평균 복구 시간 개선

---

### 형상관리 시스템 (버전 관리 시스템)

> 조직의 핵심 자산인 소스코드의 개정과 백업 절차를 자동화하여 오류 수정 과정을 도와줄 수 있는 시스템
>
> 시스템 개발 중 어떤 의미 있는 변화들을 관리하는 체계

- 의미 있는 변화들: 기능 개선, 오류 수정, 고객 요구사항 변경 등에 의한 소스코드 또는 산출물의 변경
- 수행 기능: 여러 개발자들이 협업하여 코드를 작성하고 관리할 수 있는 기능
  - 소스코드의 백업 및 이전 버전으로 롤백 기능 등 수행



### 형상관리 시스템 (버전 관리 시스템)을 사용하는 이유

- 잘못되었을 때 복구를 돕기 위해서

- 프로젝트 진행 중 과거의 어떤 시점으로 돌아갈 수 있게 하기 위해서

- 여러 사람이 같은 프로젝트에 참여할 경우,

  각자가 수정한 부분을 팀원 전체가 동기화하는 과정을 자동화하기 위해서

- 소스코드의 변경 사항을 추적하기 위해서

- 소스코드를 주가 수저했는지 추적하기 위해서

- 대규모 수정 작업을 더 안정하게 진행하기 위해서

- 가지치기(Branch)로 프로젝트레 영향을 최소화하면서 새로운 부분을 개발하기 위해서
- 통합(Merge)로 검증이 끝난 후 새로이 개발된 부분을 본류에 합치기 위해서
- 많은 오픈 소스 프로젝트에서 어떤 형태로든 버전 관리를 사용하고 있기 때문에
- 코드의 특정 부분이 왜 그렇게 쓰여졌는지 의미를 추적하기 위해서



### 형상 관리 도구

- 소스코드를 작성하고 관리하는 모든 개발자뿐만 아니라 디자이너, 기획자 등 

  파일(프로젝트)에 대한 이력 관리가 필요한 경우에는 반드시 필요한 도구

- 상용 (유료)
- 오픈소스 (무료)
  - Git / Subversion(SVN), CVS, Mercurial 등



### Git

> 프로그램 등의 소스코드 관리를 위한 분산 버전 관리 시스템

- 여러 명의 개발자가 특정 프로젝트를 자신의 컴퓨터로 협업하여 개발하면서 버전을 관리할 수 있는 시스템



### Git 의 버전 관리 방식

- 중앙 서버 컴퓨터와 여러 개의 컴퓨터들이 연결되어 모두 같은 버전의 데이터 베이스 유지 
- 업데이트될 때 마다 최신 버전이 자동으로 생성
- 파일들이 최신 버전으로 모든 컴퓨터에서 유지 



### Git의 특징

- 빠른 속도 (대형 프로젝트 사용하기 좋음)
- 단순한 구조
- 비선형적인 개발 (수 천 개의 동시 다발적인 브랜치)
- 완벽한 분산 기능 
- Github를 통해 웹 브라우저를 사용해서 누구나 저장소(Repository)를 쉽게 만들어 사용할 수 있음



### Github

- 각 개발자들이 진행한 개발 변경 사항을 온라인에서 확인 가능한 서비스
- 오픈 소스 배포 시 대부분 Git을 통해 배포 및 관리
- 저장 공간 무료 제공: 단 모든 코드 공개해야 함 (강제 오픈 소스)
- 아니면 Private 저장 공간 제공 (유료 계정 사용)
- Repository push, pull 속도 빠르고 안정적
- 다른 형상관리 툴과 호환성 좋음



### 버전 관리 기법

- 로컬 버전 관리
- 중앙 집중식 버전 관리
- 분산 버전 관리



#### 로컬 버전 관리

- 이전의 디렉토리 파일 복사 방법

- 일반적으로 소스코드 또는 문서의 버전을 관리하기 위한 방법

- 간단하고 자주 사용되는 방법이지만 작업 디렉토리를 잘못 지우거나 

  실수로 파일을 잘못 변경 또는 복사할 수 있음

- 그래서 간단한 데이터베이스를 사용해서 파일 변경 정보 관리



#### 중앙 집중식 버전 관리

> Centralized Version Control System: CVCS

- 파일을 관리하는 별도의 서버 존재
- 클라이언트가 중앙 서버에서 파일을 받아서 사용
- 장점: 누가 무엇을 하고 있는 지 관리자가 파악 가능
- 단점
  - 중앙 서버 다운 시 협업 불가, 작업 백업 불가
  - 중앙 데이터베이스의 하드디스크에 문제가 발생하면 프로젝트의 모든 히스토리를 잃게 됨



#### 분산 버전 관리 시스템

> Distributed Version Control System (DVCS)

- 모든 클라이언트에 서버의 저장소를 전부 복재
- 서버에 문제가 생기면 이 복제물로 작업 진행
- 리모트 저장 존재
- Git, Mercurial이 대표적



---

### Git 사용법

- Github에 새 저장소 (Repository) 생성 / 삭제
- STS(또는 이클립스) 에서 Github Local Repository 생성하고
- Github Repository 복제
- Local Repository에 프로젝트 추가 
- 프로젝트 게시: Github에 올리기
- Git Repository에서 프로젝트 가져오기 (Local Repository에 복제)
- Fork / Branch / 수정 작업 / Full Request / Merge



---



###  게시



1. 새 저장소 생성 (Repository 생성)

2. 로컬 리포지토리 생성 - 복제

3. 프로젝트 게시 순서

   1) Share Project

   - 프로젝트 우클릭 (Team/Share Project)

   2) Git Repository 선택 (C:\users\rangs\git\spring 선택하고 Finish)

   3) 로컬 리포지토리에 추가된 프로젝트 확인

   4) Commit 할 항목 선택: Working Tree 선택된 상태에서 

   - 오른쪽 아래 [Git Stagin] 탭에서 Add (초록색 아이콘) 클릭하면 
   - 아래 Staged Changes로 이동
   - 오른쪽 [Commit Message] 입력 ("Initail Upload")
   - Commit 버튼 클릭

   5) Push: 로컬 리포지토리 맨 위의 spring[main]에 우클릭: Push to origin

   - Login 정보 입력 / Close

   6) Github에서 확인: Repository 선택하고 프로젝트 내용 확인 



3. 프로젝트 게시 순서 (프로젝트에서 Push)

   1) Share Project

   2) Git Repository 선택 (C:\users\rangs\git\spring 선택하고 Finish)

   3) Commit 할 항목 선택: 프로젝트 우클릭: Team / Add to Index → 아래 Staged Changes로 이동

   ​										   프로젝트 우클릭: Team / Commit

   ​										   오른쪽 [Commit Message] 입력 ("Initail Upload")

   ​										   Commit 버튼 클릭

   4) Push: 프로젝트 우클릭: Team / Push to Origin

---

### 로컬 리포지토리에서 프로젝트 가져오기 

​	1) 로컬 리포지토리에서 가져오려는 프로젝트 우클릭 → Import Project

​	2) import source 선택 

​	3) import 된 프로젝트 확인

---

### 리포지토리에서 프로젝트 삭제

- Github 사이트에서는 프로젝트만 삭제 안됨: 리포지토리 전체 삭제만 가능
- Command로는 삭제 가능

#### 삭제 방법

1. 로컬 리포지토리에서 프로젝트 삭제
2. Commit: Commit Message 입력 ("XXX 삭제")
3. Push to Origin

---

### 프로젝트 수정 작업

- jsp 파일 내용을 수정

- 프로젝트 수정하면 로컬 리포지토리에도 반영
- 프로젝트에서
  - Team / Add to Index
  - Team / Commit : Commit Message 입력 / Commit 버튼 클릭
  - Team / Push to Origin

---

### Fork / Pull Requests / Merge

- Fork: 다른 사람의 Github 저장소를 복사하여 내 저장소에 붙여넣기 하는 기능

- Pull Requests: Fork로 가져온 코드 수정 후 게시하고 가져가라고 요청하는 것 - 메일 전송

- Merge: 변경된 사항을 통합 (반영) - confirm: 확인 했다고 메일 전송

- branch (가지): Root 프로젝트로 부터 파생된 프로젝트 

   						 코드 전체를 복사해서 독립적으로 개발하는 것 (자신 만의 버전)

  ​						  독립된 working directory

- 팀 프로젝트 저장소 생성

  - 팀장 선출

  - 팀원: branch로 Fork 해서 작업 수행 

    ​          수정된 내용 올리고 Pull Requests 해서 팀장에게 가져가라고 메일 전송

  - 팀장: 메일 확인하고 Merge 작업 수행 / confirm 메일 전송

  