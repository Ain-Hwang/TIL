# Screen programming

#### ABAP program type

* Executable program \(type 1\) //단독실행 가능
* module pool \(type m\) //단독실행가능 
* Function group \(type f\) //단독실행 x 재사용 가능 , 테스트실행 가
* Interface \(type j\) //단독실행 x 재사용 가능, oop관련
* Class pool \(type k\) //단독실행 x 재사용 가능, oop관련
* Include program \)\(type i\) //단독실행 x 재사용 가능

#### module pool program 

리포트 프로그램과의 차이 점은 리포트 프로그램은 프로그램이 자동으로 생성해주는 1000번 스크린\(selection screen\)을 사용한다는 것이고, 모듈풀\(온라인\)프로그램은 개발자가 직접 생성한 일반 스크린을 사용한다는 것이다. 리포트 프로그램이 dbtab에서 조회한 데이터를 화면에 뿌려주는 것이 주목적이고 모듈 풀 프로그램은 데이터를 조회/수정/삭제/생성하는 등의 데이터 관리를 위한 것이 주목적이다.

#### type M 프로그램을 개발하기 위한 전체 프로세스 3가지 영역

1  screen 정의

-1: 스크린의 구성

* screen attribute: 스크린 속성은 스크린 번호, 타입, 이름, 내역, 창 크기, 다음 화면을 정의하고 sap시스템에 스크린 오브젝트를 연결하게 된다.
  * screen painter에서 설정
  * 스크린 
* screen element: 스크린 요소들은 사자가 데이터르 조회하고 입력하는 gui화면을 디자인하는 데 사용된다. 텍스트 필드, input/output field, 체크박스, 라디오 버튼 등과 같은 스크린의 구성요소를 정의한다.
* screen field: 스크린 필드의 속성은 메인 스크린 필드의 데이터 타입과 길이 등을 정의하는 부분이다.
* screen flow logic: 사용자의 액션에 반응하게 되 스크린의 PAI와 PBO와 관련돼 절차적으로 수행해야할 부분을 정의한다.



