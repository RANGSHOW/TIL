 스타일 시트 (CSS) 
 - Cascading Style Sheets : 계단형 스타일 시트
 - 단계적으로 스타일 적용
 - 여러 스타일이 겹치면 맨 마지막 스타일 적용
 - HTML의 레이아웃 배치 등의 한계를 보완하기 위해 개발된 독립적인 언어
 - 일정 기능을 미리 지정하여 여러 부분에 동일하게 적용해서 사용 
 - 가능한 작업 : HTML 문서 내의 글꼴 종류, 크기, 색, 배경, 테두리, 레이아웃 배치, 여백 등 지정
 - 다양한 효과, 애니메이션 등 가능

 스타일 시트 장점
 - 자유롭게 웹 문서를 편집
 - 통일감 있는 문서 작성 : 한 번만 정의하고 여러 문서에 일관되게 적용 가능
 - 편리한 문서 관리
 	- 외부 스타일 시트 파일 사용할 경우 여러 웹 문서에 동일하게 적용가능
 	- 한 번만 수정해서 모든 웹 문서의 스타일 동시에 변경 가능

 스타일 시트 적용 방법
 (1) 문서 내부에 정의 (Embedded Style)
 (2) 외부 문서로 작성해서 연결하여 사용 (Linked Style)
 (3) 태그에 직접 정의 (Inline Style)


(1) 문서 내부에 정의 (Embedded Style)
- <head> 태그 내에 삽입
- 현재 문서 전체에 특정 효과 주기 위해 사용
<head>
	<style type="text/css">
		선택자 { 속성:값; }
	</style>
</head>

(2) 외부 문서로 작성해서 연결하여 사용 (Linked Style)
<head>
	<link rel="stylesheet" type="text/css" href="외부 css 파일명">
</head>

 	<link rel="stylesheet" type="text/css" href="myStyle.css">

 (3) 태그에 직접 정의 (Inline Style)	
 <body style="color:blue;">
 	
-------------------------------------------------------------------
 스타일 시트의 기본 형식
 - 선택자 (selector) : 스타일을 적용할 대상
 	- 태그, 아이디,  클래스, 속성
 - {속성:값;} : 적용하고자 하는 속성과 값 (크기, 색상, 글꼴  등)
 - 예 : 태그 선택자인 경우 : h1 {color:red; }

 선택자 유형
 (1) 태그 선택자
 (2) 클래스 선택자
 (3) 아이디 선택자
 (4) 속성 선택자
 (5) 상태 선택

 (1) 태그 선택자	 : 태그명 사용 
 - 요소(element) 선택자라고도 함
 - HTML 문서에 있는 같은 모든 태그에 동일하게 적용
 - 태그명 {속성:값;}

  (2) 클래스 선택자
  - 여러 개를 그룹화해서 동일하게 적용하기 위해 선택
  - 중복 적용
  - 사용자 정의 선택자
  - . 사용
  - 형식 
    -.클래스명 { 속성:값; }
    - 태그에 class="클래스명"이 지정되어 있어야 함
    - <태그명 class="className">  


  (3) 아이디 선택자 
  - id="xxx" 지정해서 이 아이디에 해당되는 태그를 선택

  - 아이디는 유일한 값 - 1개만 존재

  - 문서에 특정 부분에만 필요한 CSS를 적용할 때 사용

  - 식별 선택자라고도 함

  - 선택자 앞에 #붙임

  - 형식 
    - #id명 {속성:값; }
    - 태그에 id가 지정되어야 함 <태그명 id="id명">
    - `<div id="bigBox">`

    - #bigBox {   }

 

 

 

```html
text-align: center; 가운데 정렬 

<div style: box> 는 안먹힘</div>
```




​    	
​    	
​    	
​    	
​    	
​    	
​    	
​    	