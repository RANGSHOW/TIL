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

- 

---

10. 채팅창 만들기



대화 모델 연습