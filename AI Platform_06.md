## CLOVA Chatbot 서비스 만들기



#### >>> 1단계 >>>

Step 2. 도메인 생성.

Step 3. 대화 생성.

Step 3.1 학습 질문 입력하기.

Step 3.2 챗봇 답변 입력하기.

Step 3.3 챗봇 빌드하기.
			빌드 중에 메시지 출력 '베타 환경에서 테스트가 가능합니다.' - 아래 테스트 버튼 눌러서 확인

Step 4. 챗봇 테스트.



주의 사항! Basic 서비스 타입 선택 & 사용

- 하나의 도메인 당 빌드 10회까지 가능
- [빌드 10회 하고 나면 
  새로운 도메인 생성하지 말고 기존 도메인 복사해서 사용
  (또 다시 10회 빌드 가능)] X 1,000000000000!!!!



#### >>> 2단계 >>>

빌드 후

Web에서 챗봇을 구현하는 과정

1. 서비스 배포: 우측 상단에 있는 서비스 배포 클릭 (빌드 ID 확인)
2. 메신저 연동: CLOVA Chatbot Cutom 연동 설정
   - 왼쪽 상단 메뉴에서 [빌드 내역] 클릭하고
   - 두 번째 탭 [메신저 연동] 선택 →
     Custom API Gateway 와 End-point 연결이 필요합니다
     [자동 연동] 버튼 클릭 → [확인]
   - API Gateway Invoke URL: [주소 복사]
   - 아래로 내려서 [메신저 연동 설정]: Secret Key [생성] → [복사]
3. 키 생성 복사: API  Gateway 호출 URL 생성하고 Secret Key 발급



#### >>> 3단계 >>>

스프링에서 작업

1. ChatbotService 클래스 생성
2. API 코드 복사: 메소드 3개 다 복사
   - 인코딩 부분 오류 - 수정된 코드 보내줌
3. APIController에서 서비스의 main() 메소드 호출하면서 질문 전달 "넌 누구니?"
4. 콘솔창에서 결과 확인 (JSON 형식의 문자열 반환)
5. "답변 추출" JsonToString() 메소드 추가 : text
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

1. - 

---

대화 모델 연습

- 이미지 답변
- 멀티링크 답변
- jsonToString()에서 타입별로 추출



API 코드 복사 경로

- Console / AI NAVER API / Application / 개발 가이드
- AI Application Service / CLOVA Chatbot /  CLOVA Chatbot  고급 기능 상세 가이드 / CLOVA Chatbot Custon API
- 바로 가기 : CLOVA Chatbot Custon API
- CLOVA Chatbot Custon API 클릭하고 오른쪽 페이지에서[ 각 언어별 CLOVA Custom API 구현 예제]

- 메소드 3개 복사 :

  - ``` java
    public String main(String voiceMessage, String apiURL, String secretKey) {}
    → public String main(String voiceMessage) {
        String apiURL = "";
    	String secretKey ="";
    }
    ```

    

https://575d94b01a4949faa161bc91fbc7b9a3.apigw.ntruss.com/custom/v1/4646/f700ad40fb38187e9a9cafa84c728a1c31ddb5646d7f78db3cd72f43e7950d7e



R3VLTWhOWlBEcmp0c1dqTm52dUpIeHhEYnl2ZVNGc3c=



**빌드 ID:13530**



---

### 웹 페이지에서 녹음 기능

- voiceRecord.jsp
- 녹음 / 정지 버튼
  - 녹음: 음성 녹음
  - 정지: 파일로 저장 (다운로드 폴더)

---

#### [#4] 음성으로 질문하면 챗봇에서 텍스트로 답변 보내기

> (채팅창에 텍스트도 출력) + 음성

1. 음성으로 질문하며 챗봇에서 텍스트로 답변 보내기

   녹음 기능: 웹페이지에서 녹음

   - [녹음] 버튼: 음성 녹음하고 mp3 파일로 저장(다운로드 폴더에 저장): 너는 누구니? 
   - [중지] 버튼: 챗봇에서 음답: 저는 독서지도사입니다.

2. STT: Speech To Text

   - STT 기능을 사용해서 다운로드 폴더에 저장된 음성 파일을 텍스트로 변환
   - 변환된 텍스트를 챗봇에게 질문으로 전달
   - 챗봇이 텍스트로 답변 전달 → 채팅창에 출력



질문 녹음 (다운로드 폴더에 저장)

음성 파일을 텍스트로 변환: STT

- mp3 파일명 전달
- 다운로드 폴더에 있는 파일을 서버로 전송
- STT: 텍스트 변환

변환된 텍스트 질문으로 챗봇에게 전달

챗봇으로부터 답변 받아서 채팅창에 출력



chatForm.jsp에 녹음 버튼 추가

chatbot.js

- 녹음
- 파일 업로드: STT (clovaSTT2)
- 챗봇에게 질문 전달하고 답변 받기
- 채팅창에 출력

AIRestController 에 추가: clovaSTT2

STTService 클래스에 메소드 추가: chatbotSpeechToText(): Kor

- 파일 경로 이름 전달: filePathName
- 텍스트로 변환된 녹음 파일은 삭제 (다운로드에 있는 음성 파일 삭제): `voiceFile.delete();`

결과 확인





---

#### [#5] 음성으로 질문하면 음성으로 답변하기 ( 텍스트 답변 → 음성파일 변환: TTS)

> (채팅창에 텍스트도 출력) + 음성

- 챗봇으로부터 받은 답변을 TTS 기능 사용해서 음성으로 변환하여 출력



받은 답변을 TTS 전달하기 위한 Ajax 추가

- cllAjaxTTS() 함수 추가
- 텍스트 message 전달하고
- 답변 받으면 `<audio>` 플레이 (동적 생성하지 말고 jsp에 `<audio>` 태그 배치 (나중에 숨기기))



TTSService 클래스에 메소드 추가

- chatbotTextToSpeech(String message)
- 파일 이름이 아닌 메시지 전달



chatForm.jsp에 `<audio>` 태그 추가

- hide() 사용해서 숨기기



순서

1. chatbot.js에 추가 | cllAjaxTTS() 함수 
2. TTSService 클래스에 메소드 추가
3. AIRestController에 추가: chatbotTTS
4. 결과 확인 



---

#### [#6] 채팅창 없이 음성 채팅 ( 음성 질문 → 음성 답변)

> 중간에 클라이언트 출력 없고 서버에서 한 번에 다 처리하고 결과만 클라이언트로 전송



chatbotVoice.jsp 새로 생성

- 채팅창 없음
- 음성 메시지 녹음
- `<audio>` 태그



chatbot.js

- fileUpload()
- url: chatbotOnlyVoice
- `<audio>` 플레이만
- chatBox 삭제



AIRestController 

- 모두 전달하고 받음
  - STT → chatbot → TTS



index.jsp에 추가

결과 확인



웰컴 메시지 출력되도록 추가

chatbotVoice.js

- 파일명 없이 fileUpload("");



AIRestController 

- result="" 부분 추가

---



독서 모임 신청 시나리오
대화 : 독서 모임 신청하기
주최 : 북클럽 멀티
일자 : 2021-05-22 토
시간 : 15:00 ~17:00
소요 시간 : 2시간
장소 : 멀티캠퍼스 본관 512호
대상 도서 : 지구의 눈물
참가비 : 5,000원 (음료)
찾아 오는 길 : 이미지 http://www.mult.com/map/
주차 안내 : 이미지
문의 : 010-1234-1234
이메일 : mult@book.com
신청 : https://www.multicampus.com/kr/index.html

----

기본 답변: 독서 모임 시간 문의

이미지 답변

- 이미지만: 약도