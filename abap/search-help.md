# Search Help

search help는 input  help를 제공하는 하나의 방법이다. input help는 화면 field에서 사용자가 입력할 수 있는 값 \(possible value\)를 조회하는 sap 표준 기능이다.

### Search help를 이용한 input help 제공하는 법

search help를 생성해 table field에 할당한다. 그리고 screen field는 table field의 속성을 상속받아 input help로 사용할 수 있다. table field에 search help가 존재하지 않으면 check table의 데이터와 domian의 fixed value가 input help에 연결된다. 그리고 static input help라고 부르는 DATS와 TIMS 타입은 달력과 시간 구조로 정의되어 있는 input help를 이용한다.

### Search help 종류 

#### 1. elementary  search help

* 기본 탐색 도움말
* 하나의 tab으로 구성됨
* selection method의 데이터를 활용

#### 2. Collective Search help

* 일괄 탐색 도움말
* 여러 개의 tab으로 구성됨elementary search help의 조합으로 구성됨

### elementary search help

유저로 부터 데이타를 import받아서 -&gt; selection method로 possible entry 구성 -&gt; 선택된 데이터 -&gt; 유저에게 export

* selection method: tab, view가 들어갈 수 있다. maintenance view는 하나의 프로그램이라서 들어갈 수 없다. 그래서 대신 쓰는게 help view이다.

### selection method 

search help는 실행 시점에 데이터베이스에서 데이터를 가져와서 적중 리스트 \(hit list: 사용자에게  입력 가능한 리스트를 보여준다.\)를  구성하게 된다. 이 때 사용되는 데이타베이스 대상을 selection method라고 한다. selection method로느 abap dic에 table 또는 view를 사용할 수 있다. 하지만 maintenance view는 사용할 수 없다. 한 테이블에 필요한 값이 존재할 때는 selection method에 해당 체이블만 선택하면 된다. 그러나 원하는 데이터가 두 개 이상의 테이블에 존재한면 테이블 엔트리는 foreign key로 연결된 view를 이용해야한다. 

#### Dialog Behavior의 3가지 type

search help를 사용자에게 어떻게 보여줄지 결정. 

1. Dialog with value restriction
2. Display values immediately
3. Dialog depends on set of value





