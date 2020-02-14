# Search Help

search help는 input  help를 제공하는 하나의 방법이다. input help는 화면 field에서 사용자가 입력할 수 있는 값 \(possible value\)를 조회하는 sap 표준 기능이다. \(F4 help\)

### Search help를 이용한 input help 제공하는 법

search help를 생성해 table field에 할당한다. 그리고 screen field는 table field의 속성을 상속받아 input help로 사용할 수 있다. table field에 search help가 존재하지 않으면 check table의 데이터와 domian의 fixed value가 input help에 연결된다. 그리고 static input help라고 부르는 DATS와 TIMS 타입은 달력과 시간 구조로 정의되어 있는 input help를 이용한다.

### Search help 종류 

#### 1. elementary  search help

* 기본 탐색 도움말
* 하나의 tab으로 구성됨
* selection method의 데이터를 활용

#### 2. Collective Search help

* 일괄 탐색 도움말
* 여러 개의 tab으로 구성됨
* elementary search help가 여러개 모여 만들어진 

### elementary search help

유저로 부터 데이타를 import받아서 -&gt; selection method로 possible entry 구성 -&gt; 선택된 데이터 -&gt; 유저에게 export

* selection method: tab, view가 들어갈 수 있다. maintenance view는 하나의 프로그램이라서 들어갈 수 없다. 그래서 대신 쓰는게 help view이다.

### selection method 

search help는 실행 시점에 데이터베이스에서 데이터를 가져와서 적중 리스트 \(hit list: 사용자에게  입력 가능한 리스트를 보여준다.\)를  구성하게 된다. 이 때 사용되는 데이타베이스 대상을 selection method라고 한다. selection method로 abap dic에 table 또는 view를 사용할 수 있다. 하지만 maintenance view는 사용할 수 없다. 한 테이블에 필요한 값이 존재할 때는 selection method에 해당 테블만 선택하면 된다. 그러나 원하는 데이터가 두 개 이상의 테이블에 존재한면 테이블 엔트리는 foreign key로 연결된 view를 이용해야한다. 

#### Dialog Behavior의 3가지 type

search help를 사용자에게 어떻게 보여줄지 결정. 

1. Dialog with value restriction
2. Display values immediately
3. Dialog depends on set of value

#### LPOS SPOS

search help의 위치를 결정하는 것이다. dialog box의 위치를 결정하게된다.

#### Search help의 import와 export 파라미터

input help가 호출될 때 화면에 이미 입력된 값을 조건으로 하여 적중 리스트를 제한할 수 있다. 즉 input help를 호출하면 적중 리스트가 조회된다. 이때 input help를 갖는 field를 context field라고 하며 적중 리스트에서 선택된 line을 input template라고 한다.

search help의 interface는 input help에 사용될 수 있는 context data\(import\)와 화면에 반환 되는 input template\(Export\)로 정의할 수 있다.

### search help의 활용

search help는 3가지 방법으로 field에 추가 될 수 있다. 

* Data element에 search help추가
  * data element의 속성을 상속받는 모든 스크린 필드에 search help 가 자동으로 연결된다.table field에 search help 추가
* table field에 search help 추가
  * table field에 search help를 추가하면 table field를 참고하는 모든 스크린 field에 search help가 연결된다. search help의 export 파라미터가 테이블 필드에 할당되면 사용자가 리스트를 선택할 때 파라미터와 같은 이르므이 스크린 필드들에 값이 반환된다. 또한 import파라미터가 테이블field에 할당되면 스크린field에 입력된 값을 적중 리스트의 값을 제한하게 된다.
* screen field에 search help추가 
  * screen painter를 이용해 스크린 필드에 직접 search help를 할당할 수 있다. 이 경우에는 해당 스크린 필드에만 search help가 작동하게 된다. \(dialog mode\)

#### Search help 호출되는 우선순위

1. screen field에 추가된 search help
2. table field에 추가된 search help
3. check table의 input help기능
4. data element에 추가된 search help
5. domain의 fixed value 
6. time 또는 calender help\(예, 날짜 타입 - dat field\)

#### selection method를 활용한 search help의 view\(=help view\)

primary table에 해당하는 값을 secondary table에서 모두 가져와 보여 주는 것이 help view =outer join 모습

#### search help의 3가지 유형

* List box 형태
* control \(amodal=밖에 창들 핸들링 가능: lpos, spos로 하는 것\) 
* dialog\(modal=바깥 창 핸들링 불가능\)

#### append search helps

append structure와 비슷하다. sap collective search help에 append search help를 이용해서 sap standard search help에 customer search help 추가하는 법 

#### search help exits

search help할 때 여러 옵션을 줄 수 있다.













