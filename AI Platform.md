## 프로젝트 개요

> 유명인 얼굴 인식

- 스프링 프로젝트 생성

- NAVER AI Platform에서 Application 등록

- 인증키 받아서 API를 통해 결과 받아 JSP 뷰페이지로 출력



---



### 스프링 부트 프로젝트 생성



프로젝트 명: naverAI

패키지 명: com.multi.naverai

Dependencies

- JDBC API / Oracle Driver / MyBatis Framework
- Spring Web



- application.properties 파일에 설정 추가 
- pom.xml에 의존성 추가
  - jsp
  - devtools
  - json
- veiws 폴더 생성
  - src/main/webapp 폴더에 WEB-INF / views 폴더 추가
  - index.jsp 생성



- index.jsp 개요
  - 각  AI 서비스를 사용하기 위한 메뉴 항목 하나씩 추가
  - 컨트롤러에게 요청 → 각 서비스마다 Service 클래스 생성해서 처리 → Naver AI API 요청
  - 컨트롤러에서 뷰 페이지로 출력 ← 결과를 컨트롤러에게 반환

패키지 생성: com.multi.aiservice

- 컨트롤러 생성: APIController

  

---



### Naver AI Platform 접속

Application 등록

인증키 발급 (코드에서 사용)

개발 가이드: https://api.ncloud-docs.com/docs/ai-naver-clovafacerecognition-celebrity

- 유명인 얼굴 인식 API 개요
- 감지된 얼굴의 수
- 감지된 얼굴을 분석한 정보
  - 닮은 유명인 정보
  - 해당 유명인물 닮은 정도
- 요청 URL / 헤더 / 응답 필드 확인
- 요청 예시: JSON 형식
  - key: faces:
  - value: [] 리스트로 구성
  - faces 를 추출해서 리스트를 반복 (for 문) 하여 value 와 confidence 추출
- API 예제: java 부분을 복사해서 사용할 것임
- 변경할 부분
  - clientID / clientSecret
  - uploadFile: 파일 경로 및 파일명
- 출력: JSON 형식의 문자열로 콘솔창에 출력



이미지 복사해서 다음 디렉토리에 저장

- C:/ai/xxx.jpg

이미지 파일

- 1인 (여성 / 남성 / 연령별)
- 2인 / 5인 구성된 이미지 파일 준비



작성 클래스

- CelebrityVO
- CFRCelebrityService
- APIController (이미 작성했음)
- index.jsp에 링크 추가 (요청 맵핑)
- 실행시켜서 콘솔창에 결과 출력
  - {"info":{"size":{"width":325,"height":153},"faceCount":2},
    		"faces":[
      				{"celebrity":{"value":"주원","confidence":1.0}},
      				{"celebrity":{"value":"강동원","confidence":0.856215}}
      		]}
  - JSON 형식의 문자열로 출력



우리가 추출할 내용

- "faces"
- "celebrity"
- "value" / "confidence"
- "강동원" / 0.654626



- JSON 형식의 문자열에서 "confidence" 와 "value" 추출해서

- CelebrityVO 저장

- 이 작업을 수행할 메소드 추가 : 서비스 클래스

- CFRCelebrityService 클래스에 jsonToVoList() 메소드 추가 

  1. 결과로 받은 JSON 형식의 문자열을 전달받아서 
  2. "confidence" 와 "value"를 추출해서
  3. CelebrityVO 저장하고 리스트에 추가
  4. CelebrityVO 리스트를 clovaFaceRecogCel() 메소드에게 반환
  5. 그러면 clovaFaceRecogCel()는 이 결과 리스트를 컨트롤러에게 반환
  6. 컨트롤러는 뷰 페이지에 출력

  

  - clovaFaceRecogCel() 메소드 호출



---



celebrityResult.jsp 페이지 윗부분에 (제목 위에) 파일 업로드 기능 추가

파일 선택하면 → 서버 (C:/ai/폴더로 업로드)

- AI API 호출할 때 ai로 경로로 지정해서 서버에서 파일을 읽어서 전송할 수 있도록 기능 추가