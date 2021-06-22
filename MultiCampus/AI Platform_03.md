c.f. 어플리케이션 추가 

- 변경 → 원하는 어플리케이션 클릭



## ***Object Detection*** (객체 탐지)



1. 기본: 서비스 API 호출 결과를 JSON 형식 문자열로 출력
   - ObjectDetectionService 클래스 생성: objectDetect() 메소드 추가
     - API 코드를 objectDetect() 메소드를 붙여넣기
   - APIController에서 추가 
   - index.jsp에 링크 추가
   - 이미지: c:/ai0/aminal2.jpg
   - 실행해서 결과 출력: 콘솔창에서 확인

2. REST API @ RestController 사용
   - ObjectVO: name, x1, y1, x2, y2
   - jsonToVoList() 메소드 추가 (ObjectDetectionService 클래스에 추가)
     - name, x1, y1, x2, y2 값 추출해서 VO에 담아 List 생성해서 반환 
   - objectResult.jsp 생성: 파일 업로드 / 결과 출력
   - object.js (Ajax): formData 보내고 / Result 받고
   - (drawCanvas: 이미지 위에 탐지한 객체에 바운딩 박스 표시 - 사각형 표시)
   - index.jsp (→ APIController)
   - APIController 변경
   - 결과 확인: 사각형 그리기 어려우면 이 부분 하지말고
     name, x1, y1, x2, y2 출력



- StringToVoList 마무리하기

---

## ***CLOVA Speech Recognition (CSR)***

- 음성 데이터를 인식해서 텍스트로 변환하여 전달
- mp3 파일 전송해서 결과 텍스트 받아서
- 브라우저에 텍스트 출력, 파일로 저장
- 음성 인식에 사용할 언어
  - Kor: 한국어
  - Jpn: 일본어
  - Eng: 영어
  - Chn: 중국어 
- 응답: 텍스트(String)



CSR (Speech-To-Text: STT)

1. 기본: 서비스 API 호출 결과를 JSON 형식 문자열로 출력
   - STTService 클래스 생성: clovaSpeechToText() 메소드 추가
     - API 코드를 objectDetect() 메소드를 붙여넣기
   - APIController에서 추가 
   - index.jsp에 링크 추가
   - 실행해서 결과 출력: 콘솔창에서 확인

2. REST API @ RestController 사용
   - jsonToString() 메소드 추가: 텍스트 추출
   - STTService 클래스 변경
   - AIRestController에 추가
   - APIController 변경
   - sttResult.jsp 생성
     - 파일 업로드 추가
     - 추출된 텍스트 추출
   - stt.js 생성 (Ajax)
   - index.jsp에 링크 추가 
   - 결과 확인
     - 음성 파일 (mp3) 업로드 
     - 음성을 텍스트로 변환된 결과 출력 
       - 텍스트 출력



3. 추가 기능
   - 언어 종류 전달 기능 추가
   - 출력된 텍스트와 일치하는지 확인하기 위해 `<audio>` 태그로 플레이하는 기능 추가
   - 결과를 받은 텍스트를 파일로 저장하는 기능 추가





- `<audio>` 태그 추가 해서 업로드한 mp3 파일
  - sttResult.jsp에 `<audio>` 태그 추가 
  - stt.js 에서 `<audio>` 의 src 속성 설정 (업로드한 파일로 설정)
- 언어 종류 전달 기능 추가
  - sttResult.jsp의 `<form>` 태그 안에 `<select>` 태그 추가
    - stt.js 변경 필요 없음 (formData 안에 다 포함되어 전송)
    - @RequestParam() 추가하면 됨
  - 서비스 코드 변경 
- 결과로 받은 텍스트를 파일로 저장하는 기능 추가
- 추출된 텍스트를 파일로 저장하는 메소드 추가
  - resultToFileSave() 메소드에서 파일 저장 기능 구현 
- 저장 디렉토리: C:/ai/ 폴더에 저장