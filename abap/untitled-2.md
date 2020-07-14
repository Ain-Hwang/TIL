# ALV

### ALV \(Abap List Viewer\)

* 리스트 화면에 데이터 조회를 가능하게 하는 것 
* ALV의 기능: 기본적인 사무 작업\(데이터 조회, 수정, 삭제 등\) 포함된 패키지 프로그램을 제공한다. 
  * 정렬기능, sum avg같은 계산 수행,  열크기, 레이아웃변경 등등
* report 프로그램 기능과 비교하자면: write 구문 사용은 단순 list 화면만 구성 가능 \(편집 불가능\)
* 사용방법 GRID 컨트롤\(Class\), 함수\(function\) 

### ALV 사전 필요 작업

1. 프로그램 생성
2. 인터널 테이블 선언 \(mian program에서 변수 선언과 select 구문을 써줌 \)
3. 데이터의 구조\(필드카탈로그\) alv grid 컨트롤이 스크린에 조회되는 구조 정의 ALV grid 컨트롤에서 정의되는 데이터의 구조, 기술 속성 내역과 같은 정보 함유함. 일반적으로 abap dic 의 테이블 또는 구조체를 이용 또는 인터널 테이블의 구조를 그대로 사용

### ALV의 아키텍쳐? 순서

1. Screen 생성
2. Area 생성 \(스크린의 Layout에서 정\)
3. Container Control 지정\( TOP Include에 변수를 cl\_gui\_custom\_container = ref type으로 선언하고 PBO에 패턴을 이용 Create Object를 한다. / ALV Grid Control도 같은 방법으로 선언하고 Create Object한다. \(ref type은 cl\_gui\_alv\_grid\)

![](../.gitbook/assets/image%20%28137%29.png)

![](../.gitbook/assets/image%20%28136%29.png)

위에는 Custom Container object\(go\_container2\)를 생성하고 Area\(Controlarea2\)와 연결하는 것  아래는 go\_alv\_grid2를 생성하고 상위가 go\_container2라고 지정해 assign한 것

4. SET\_TABLE\_FOR\_FRIST\_DISPLAY

![](../.gitbook/assets/image%20%28140%29.png)

 ALV Grid를 화면에 처음에 어떻게 보여줄지 설정하는 것  create object랑 같은 모듈에 선언해주면됨.

![](../.gitbook/assets/image%20%28138%29.png)

원래는 이렇게 설정하는게 많음 













