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



### &lt;Ok\_code&gt;

screen element list와 top에 ok\_code를 선언해 두어야 사용가 가능

SY-UCOMM =&gt; 시스템변수를 담아서 사용하는 것 

```text
DATA ok_code TYPE SY-UCOMM. "TOP에 이렇게 선언 해줘야함 .
```

\*주의 사항 스크린마다 다른 Ok\_code를 사용하는 것이 좋다.  

ex\) 100번 스크린과 200번 스크린이 있는데  조회 버튼을 갖고 200번 스크린으로 넘어 가서 한 field에 입력 번튼을 누르게 되면? 100번 스크린에 sy-ucomm인 조회라는 기능이 없어지고 입력기능이 들어온다. 그래서 ok\_code를 스크린마다 각각 달아 주는 것이 좋다.  ok\_code100, ok\_code200 이런식으로 



### &lt; on-input vs on-request &gt; 

필드의 결과 값이 영향을 받을 대 on request를 사용하는 것



### Sub screen - tab strip \(거의 type p만 사용\) 

* nomal\(none\) -  여러 탭이 sub area 를 하나 사용하는 것
* type p - 각각의 탭 마다 sub area를 따로 사용하는 것 



































