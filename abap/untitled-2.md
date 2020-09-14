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
3. Container Control 지정\( TOP Include에 변수를 cl\_gui\_custom\_container = ref type으로 선언, call screen을 해줌 / 해당하는 screen의 PBO에 패턴을 이용 Create Object를 한다. / ALV Grid Control도 같은 방법으로 선언하고 Create Object한다. \(ref type은 cl\_gui\_alv\_grid &gt; 이거는 se24에서 확인 할 수 있\)

![](../.gitbook/assets/image%20%28137%29.png)

![](../.gitbook/assets/image%20%28136%29.png)

위에는 Custom Container object\(go\_container2\)를 생성하고 Area\(Controlarea2\)와 연결하는 것  아래는 go\_alv\_grid2를 생성하고 상위가 go\_container2라고 지정해 assign한 것

4. SET\_TABLE\_FOR\_FRIST\_DISPLAY

![](../.gitbook/assets/image%20%28140%29.png)

 **ALV Grid를 화면에 처음에 어떻게 보여줄지 설정하는 것**  create object랑 같은 모듈에 선언해주면됨.

![](../.gitbook/assets/image%20%28138%29.png)

원래는 이렇게 설정하는게 많음 

![](../.gitbook/assets/image%20%28141%29.png)

refresh도 해줄 수 있음 이런 class의 method는  se24에서 method 마다의 type과 파라미터 값을 확인할 수 있다. 

alv에 담길 데이타들은 &gt;&gt;&gt;

1. initialraztion에서 sy-datum\(현재날짜\)를 function을 사용해서 월에 1부터 마지 일자까지 multi select값을 미리 줄 수 있다
2. at selection screen &gt; 화면제어 멀티셀렉션을 단일 필드로 받게 할 수도 있고, 제대로 값이 들어왔는지 확인 할 수 있음
3. start of selection &gt; 입력 받은 데이터를 받아서 select 문을 사용해 internal테이블값을 받아옴
4. end of selection &gt; call screen nnn.  를 해줌 

ALV는 각종 설정을 줄 수 있음\(save, variant 같\)

























