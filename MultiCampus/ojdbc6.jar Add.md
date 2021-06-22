## ojdbc6 라이브러리에 추가

1. C:\oracle\app\oracle\product\11.2.0\server\jdbc\lib에 있는 ojdbc6.jar 복사

2. 프로젝트에 build path에 라이브러리 추가

   1. C:/Program Files\Java\jdk1.8.0_281\jre\lib\ext에 저장하고 이클립스에서
   2. 프로젝트 이름 우클릭 Properties 창 열고
   3. Java Build Path / Libraries 탭 에서
   4. Add External Jars 버튼 눌러
   5. C:\Program Files\Java\jdk1.8.0_2811\jre\lib\ext 에 들어있는 ojdbc6.jar 파일 선택
   6. 그러면 프로젝트의 System Library 아래 Reference Library 로 추가됨
   7. 프로젝트 생성할 때 마다 설정해줘야 해서 번거롭다 => 기본 System Library에 추가

3. 기본 라이브러리 위치로 이동

   1. 위치는 어떻게 확인하나?

   2. 프로젝트 System Libraries 열면 다른 jar 파일들이 C:\Program Files\Java\jre1.8.0_281\lib\ext 확인

   3. 같은 위치에 ojdbc6.jar을 여기에 추가한다

      