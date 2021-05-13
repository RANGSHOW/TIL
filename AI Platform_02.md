## ***OCR*** 실습 (***Text OCR***)

b0xmdkRMT0ROTXVEcU5jZ3pkd0NYbmZPdFFpUXJDb28=



https://c0beeab119e6453ba48ed2e20e458d72.apigw.ntruss.com/custom/v1/8642/1d5deb675dec7f624cbd23a006ab64cbc216cba69553bed124bd7797d208b733/general



1. 기본: 서비스 API 호출 결과를 JSON 형식 문자열로 출력

   - OCRService 클래스 생성: clovaOCRService() 메소드 추가

     1. API 코드를 clovaOCRService() 메소드를 붙여넣기

     2. writeMultiPart() 메소드는 전체 복사해서 clovaOCRService() 메소드 아래에 붙여넣기
        (즉, OCRService 클래스에 메소드 2개가 됨)

   - APIController에서 추가 

   - index.jsp에 링크 추가

   - 실행해서 결과 출력

2. REST API @RestController 추가

   - 파일 업로드 
   - Ajax로 파일을 서버로 전달하고 결과를 받아서 view 페이지에 출력
   - ocrResult.jsp (파일 업로드)
   - ocr.js (Ajax)
   - AIResultController (@RestController): 컨트롤러 추가
   - @ComponentScan(AIResultController) 추가
   - 서비스 메소드 변경 (파일 이름 전달 받음)
   - APIController수정
   - index.jsp 수정
   - 실행: 텍스트가 있는 이미지 파일을 업로드
   - 결과: 텍스트 출력 



검색: OCR API → CLOVA OCR Custom API
		  CLOVA OCR Custom API
          광학 문자 인식 | CLOVA OCR Custom API 바로가기



---



## ***Pose Estimation*** (포즈 인식)

1. 기본: 서비스 API 호출 결과를 JSON 형식 문자열로 출력
   - PoseEstimationService 클래스 생성: poseEstimate() 메소드 추가
     1. API 코드를 poseEstimate() 메소드를 붙여넣기
   - APIController에서 추가 
   - index.jsp에 링크 추가
   - 이미지: c:/ai0/run.jpg
   - 실행해서 결과 출력: 콘솔창에서 확인

2. REST API @RestController 사용

   - PoseVO 생성: index, x, y
   - jsonToVOList() 메소드 추가
   - 서비스 클래스 / 메소드 수정
   - AIResultController(@RestController)에 추가
   - poseResult.jsp 생성: 파일 업로드 / 결과 출력 
   - pose.js (Ajax): formData 보내고 / result 받고
   - (drawCanvas: 이미지 위에 추출한 좌표 (0~17개)의 좌표를 표시)
   - index.jsp에 추가
   - APIController 변경
   - 결과 확인 

3. resultDiv에 출력

   코(0.223123, 0.483479) 등 출력하기