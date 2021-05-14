5월 15일 멘토링 진행 일정

1. 멘토와 진행
2. 자유회의 시간 및 발표자료 준비
3. 조별 발표 (아이디어/주제발표)
4. 멘토와 진행 (피드백)



---

## ***CLOVA Voice***



네이버 가이드에서 tts (Text-To-Speech) 가 3가지가 있는데

1개만 되고 나머지는 사용할 수 없음



우리가 사용할 수 있는 서비스 

Clova Voice : TTS (Premium)



주의!!!

String apiURL = "https://naveropenapi.apigw.ntruss.com/tts-premium/v1/tts";



텍스트를 파라미터로 입력받아 음성을 합성하여 그 결과를 반환

text → mp3, wav 반환



서비스 신청: CLOVA Voice-Prmium



### TTS (Text-To-Speech)

1. 기본: 서비스 API 호출 결과를 mp3 파일로 변환
   - TTSService 클래스 생성: clovaTextToSpeech() 메소드 추가
     - API 코드를 objectDetect() 메소드를 붙여넣기
   - APIController에서 추가 
   - index.jsp에 링크 추가
   - 이미지: c:/ai0/aminal2.jpg
   - 실행해서 결과 출력: 반환된 mp3 파일 확인
2. 언어 / 목소리 변경
   - 저장 위치 변경
3. 파일 업로드
   - 텍스트 파일 업로드
   - 파일 내용을 읽어서 텍스트로 추출해 서버로 전송
     - 텍스트 파일 읽어서 문자열 반환하는 메소드 추가: fileRead()
   - REST API: @RestController 사용
4. `<audio>` 태그 추가
5. 언어 선택 `<select>`  태그 추가



- nara: 한국어, 여성

- jinho: 한국어, 남성
- nhajun: 한국어, 아동(남)
- ndain: 한국어, 아동(여)
- clara: 영어, 여성
- matt: 영어, 남성
- carmen: 스페인어, 여성
- shinji: 일본어, 남성
- meimei: 중국어, 여성



중국어: 만나서 반갑습니다. 见到你很高兴!



---

## CLOVA Chatbot 서비스 만들기



#### >>> 1단계 >>>

Step 2. 도메인 생성

Step 3. 대화 생성

Step 3.1 학습 질문 입력하기

Step 3.2 챗봇 답변 입력하기

Step 3.3 챗봇 빌드하기 
			빌드 중에 메시지 출력 '베타 환경에서 테스트가 가능합니다.' - 아래 테스트 버튼 눌러서 확인

Step 4. 챗봇 테스트



주의 사항! Basic 서비스 타입 선택 & 사용

- 하나의 도메인 당 빌드 10회까지 가능
- [빌드 10회 하고 나면 
  새로운 도메인 생성하지 말고 기존 도메인 복사해서 사용
  (또 다시 10회 빌드 가능)] X 1,000000000000!!!!



#### >>> 2단계 >>>

빌드 후

Web에서 챗봇을 구현하는 과정

1. 서비스 배포
2. 메신저 연동: CLOVA Chatbot Cutom 연동 설정
3. 키 생성 복사: API  Gateway 호출 URL 생성하고 Secret Key 발급



#### >>> 3단계 >>>

스프링에서 작업

1. ChatbotService 클래스 생성
2. API 코드 복사: 메소드 3개 다 복사
   - 인코딩 부분 오류 - 수정된 코드 보내줌
3. APIController에서 서비스의 main() 메소드 호출하면서 질문 전달 "넌 누구니?"
4. 콘솔창에서 결과 확인 (JSON 형식의 문자열 반환)
5. "답변 추출" JsonToString() 메소드 추가 
6. REST API - AIRestController 에 추가
7. chatbotResult.jsp
   - `<input>` 태그에서 질문 입력
   - `<div id="resultDiv">`: 답변 출력
8. chatbot.js (Ajax)
9. index.jsp



결과 확인

- 입력란에 질문 입력: "너 누구니?"
- div에 바로 결과 출력: "저는 독서 지도사 입니다."

---

10. 채팅창 만들기



대화 모델 연습