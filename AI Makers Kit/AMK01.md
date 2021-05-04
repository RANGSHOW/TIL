## AI Makers Kit

- KT의 기가지니를 이용한 인공지능 스피커 개발 키트
- AMK 와 라즈베리파이라는 컴퓨터를 이용하면 직접 인공지능 스피커를 만들 수 있음



### 인공지능 스피커

- 스피커, 마이크, 컴퓨터를 하나로 결합해서
- 인공지능 기능을 이용하여 사용자와 대화할 수 있는 스피커
- 상대방의 말을 알아듣고, 질문에 대답하고, 행동할 수 있는 기능 제공
- 텍스트를 분석해서 음석으로 변환하거나, 음성을 텍스트로 변환 가능
- 사물 인터넷(IoT)와 연결되어 여러 센서 또는 장치 등 제어하는 기능



- 음성 인식 스마트 스피커 제품
  - KT 기가 지니
  - 아마존의 에코
  - 구글의 구글 홈
  - 네이버의 클로바 (프렌즈, 데스크)
  - 카카오의 카카오 미니 등
- 다양한 브랜드와 플랫폼에서 인공 지능 스피커 제공



### AI Makers Kit 활용

1. 조립
2. 내 컴퓨터에 VNC Viewer 설치
3. OS 이미지 레코딩 - SD 카드
4. 노트북에서 핫스팟 설정
   - 라즈베리파이 IP 확인
5. VNC Viewer 사용해서 원격 제어
   - 접속
     - ID: pi
     - PW: raspberry
6. AMK 따라하기

---

2. 내 컴퓨터에 VNC Viewer 설치
   - https://www.realvnc.com/en/connect/download/viewer/
   - 설치: English, Next (X 100)

3. OS 이미지 레코딩 - SD 카드

   - OS 이미지 다운로드 (34 ~ 35)
   - KT API Link 홈페이지에서 다운로드
   - OS 이미지 레코딩 (36 ~ 37)
   - 이미지 레코딩 프로그램 Echer 설치
   - SD 카드에 이미지 레코딩

4. 노트북에서 핫스팟 설정

   - 라즈베리파이 IP 확인

   - 모바일 핫스팟 키고 네트워크 이름 / 암호 복사 해놓기

     - ID: DESKTOP-ATQTJLE 8529

     - PW: !14F1h92

   - 핫스팟 연결을 위한 파일 2개 생성 (설명서에 없음)

     - ssh (확장자 없고, 내용 없음)
     - wpa_supplicant.conf
       - 이 파일 안에 네트워크 이름 / 네트워크 암호 지정
     - 2개 파일 SD 카드에 복사

---

클라이언트 키 입력

[파일매니저]에서 

home/pi/ai-makers-kit/python3 폴더로 이동

user_auth.py 우클릭 Text Editor로 열어서

- Downloads 폴더에 있는 clientKey.json 파일에 있는
- key, id, secret 복사해서 붙여넣기

---

## AMK 예제

> ai-makers-kit / python3 폴더에 예제가 ex1 ~ ex9 들어있음

터미널에서 

ai-makers-kit / python3 폴더까지 이동

: cd ai-makers-kit

: cd python3

혹은

cd ai-makers-kit/python3



예제1: 대기하고 있는 AMK를 호출하는 예제

- 호출어: 대기하고 있는 인공지능 스피커를 호출하는 명령어
- AMK에서 제공하는 호출어: '기가지니', '지니야', '친구야', '자기야'
- 4개 중에서 선택해서 사용 (다른 단어로 변경하면 인식 못함)



실행: python3 ex1_kwstest.py (ex1까지만 넣고 `tab` 입력하면 자동 완성)

결과: 

- '기가지니' 호출
- "띠리링" 소리가 스피커에서 출력되면 AMK가 호출어를 제대로 인식한 것



- 호출어 변경
  - Text Editor로 열고 "자기야"로 변경



---

### 예제 2 : 인식된 음석을 텍스트로 출력하기

- 인식된 음성을 텍스트로 바꾸어 출력하는 예제
- AMK 마이크를 통해 입력된 음성은 KT API 서버를 거쳐서 텍스트로 변환
- 음성 인식 (Speech-to-Text: STT) 기술 체험



- 음성인식(Speech-to_Text) 기술
  - 컴퓨터가 마이크와 같은 소리 센서를 통해 얻은 음성신호를
  - 단어나 문장으로 변환시키는 기술
- 음성인식이 가능한 글자 수: 100글자 이하
- python3 ex2_getVoice2Text.py
- 실행 후 스피커에 대고 말하기: "안녕하세요"
  - 음성이 문자로 변환되어 출력
  - 인식 결과: 안녕하세요

---

### 예제3: 지정된 텍스트를 음성으로 재생 (URL 반환)

- 지정된 텍스트를 ㅇ므성으로 바꾸어 음성을 들을 수 있는 인터넷 주소(URL)을 제공하는 예제
- 사전에 입력된 텍스트는 음성합성(TTS) 기술을 사용해서 음성으로 변환

1. python3 ex3_getText2VoiceUrl.py 실행하고
2. copy URL
3. 웹 브라우저에서 Paste and Go

### c.f. `yield`

``` python
def generate_request():
    ...
    yield message
    
    rms = audioop.rms(...)
```

- return 과 비슷하게 사용되는 키워드
- 함수가 제너레이터를 반환
- yield 호출되면 함수는 그 시점에서 일시 정지
- 그 시점에서 함수 안에 선언되어 있던 변수 
- next()를 통해 다시 실행되면 yield 바로 다음 라인부터 이어서 실행을 이어나감



### c.f. ***generator***

- 메모리를 효율적으로 사용하면서 반복을 수행하도록 돕는 객체

- 제너레이터는 모든 값을 메모리에 담고 있지 않고 그 때 그 때 값을 생성해서 반환

  ``` python
  def yieldFunc():
      for i in [1, 2, 3]:
          yield i
          print("리스트 요소 출력")
  
  result = yieldFunc()
  print(result)  # <generator object ... >
  print(next(result)) # => 1
  print(next(result)) # => 2
  ```

---

### 예제 4: 지정한 텍스트를 음성으로 재생 (wav 생성)

- 지정된 텍스트를 음성으로 바꾸어 wav 형태의 합성된 음성 파일을 제공하는 앱

1. ex4_getText2VoiceStream.py 열고 출력할 텍스트확인
   - 실행:  `python3 ex4_getText2VoiceStream.py`
     - 출력되는 음성이 지정된 텍스트와 동일한지 확인
     - 생성된 testtts.wav 파일 확인
       - `aplay testtts.wav`
     - testtts.wav 파일 재생
2. 텍스트 변경 / wav 파일명 변경
   - 생성된 wav 재생

- 사용자의 인증 API 키를 받아서 GRPC 패키지 사용

  - GRPC: 라즈베리파이가 서버와 통신하기 위해 사용하는 프로토콜
  - channel = grpc.secure_channel('{}:{}'.format(HOST, PORT), UA.getCredentials())
  - stub = gigagenieRPC_pb2_grpc.GigagenieStub(channel)

  ```python
  channel = grpc.secure_channel('{}:{}'.format(HOST, PORT), UA.getCredentials())
  stub = gigagenieRPC_pb2_grpc.GigagenieStub(channel)
  ```

  - 사용할 언어를 설정 (한국어의 경우 lang= 0)
    message.lang = 0

---

### 예제 5: 지정한 텍스트에 대한 대답을 텍스트로 받기

- 미리 저장해둔 질문에 대한 대답을 텍스트로 받는 예제
- KT API 서버자가 사용자의 질문을 분석하고, 알맞은 결과를 AMK로 전달
- 실행: `python3 ex5_queryText.py`
- 현재 질의한 내용: 안녕
- 질의에 대한 답변: 안녕하세요? 너무 반가워요.



- 텍스트, userSession, deviceId
  - 텍스트: 답변을 받기 위한 질문
  - userSession: 질의 문맥을 유지할 때 필요한 값으로 문맥에 따라 다르게 설정
  - diviceId: 해당 AI 스피커의 정보, 디바이스에 따라 다르게 설정. 일반적으로 MAC 주소로 설정
  - message.queryText = text
  - message.userSession = "1234"
  - message.deviceId="yourdevice"



- MAC 주소 확인 명령어: ifconfig

---

### 예제6: 음성으로 질문하고 텍스트로 대답 받기

- 음성 인식 기술과 음성 합성 기술을 사용하는 예제
- 사용자의 질문(음성)에 대한 답변을 텍스트로 받음



- 실행: `python3 ex6_queryVoice.py`
- 결과 확인
  - 마이크에 대고 원하는 질문을 하면 대답 출력
    - 안녕하세요 / 반가워요
    - 지금 몇 시야? / 지금 바로 이 순간을 즐기세요
    - 누구야? / 아이돌 바로 ...

---

### 예제7: 호출어로 AMK를 호출하고, 인식한 음석을 텍스트로 출력

- 호출어와 음성인식 결합 예제
  -  ex1와 ex2 import 해서 사용
  - ex1: 호출어 detect() 
  - ex2: 음성을 텍스트로 변환 getVoice2Text()
- 실행: `python3 ex7_kwsstt.py`

---

### 예제 8: 호출어로 AMK 호출하고, AMK와 대화하는 예제

---

### 예제 9: 버튼을 눌러서 대화하기

- 호출어를 통해서 AMK를 호출하는 방법이 아닌

  AMK에 부착된 아케이드 스위치를 눌러서 호출하고 대화하는 예제

- `python3 ex9_btnSttDss.py`

  - 버튼 누름
  - '띠리링' 1초 후에 질문
  - AMK가 질문에 대해서 음성으로 답변

