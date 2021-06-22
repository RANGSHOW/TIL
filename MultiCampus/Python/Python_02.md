## 데이터 전처리

1. 아나콘다 설치: C:\Anaconda3

2. 환경변수 설정

   - 내 PC / 속성 / 고급시스템 설정 / 환경변수

     시스템 변수에서 Path 편집

     새로 만들기 / 찾아보기
     
     - C:\Anaconda
     - C:\Anaconda\Scripts

3. 파이썬 버전 확인: Python 3.8.5

4. 아나콘다 프롬프트 열어서 python --version

5. 주피터 노트북 - 사용 폴더 설정

   - 주피터 노트북에서 자동 설정된 값 삭제
   - 구성 파일 생성해서 홈 디렉토리 설정

   - Jupyter Notebook 위치 찾아서 속성 창 열고 대상에서

     "%USERPROFILE%/" 삭제

6. 아나콘다 프롬프트 열고

   jupyter notebook --generate-config



7. 웹 프라우저를 크롬으로 설정

   크롬 실행 파일 경로 복사

   jupyter notebook --generate-config 의 browser에 설정

   - 크롬 위치 C:\ProgramData\Microsoft\Windows\Start Menu\Programs