# Report programming

report program = execute program = interactive program 

database에서 원하는 data를 추출하고 해당 data를 정보로 활용할 수 있는 구조로 변경하여 리포트 형식으로 조회한다. 프로그램 자체적으로 직접 실행\(단독실행\)이 가능하며 SUBMIT이라는 키워드로 다른 프로그램 호출 가능 = 데이타를 읽고 조회하는데 가장 적합 \(type:1\)



### 프로그램 속성

* Executive program \(1 TYPE\) 
  *  t-code없이 se38에서 직접 실행가능
  * SELECTION SCREEN과 Output List로 구성
  * Logical DB 사용가능
* Module pool program \(M TYPE\)
  * Screen Painter 
  * Screen module processing
  * t-code나  menu function에 의해서만 실행
* Include \(I TYPE\)
  * 다음 프로그램에서 include로 호출되는 내장형 프로그램
* Subroutine\(S TYPE\)
  * External PERFORM 구문에서 호출해서 사용 가능한 FORM문을 구성
* 기타유형 
  * F~K는 program attribute에서 변경할 수 없으며 각각의 builder에서 관리함

2 Status\(상태\)

* 프로그램 상태에 따라 특정 utility 사용 불가 ex&gt; 시스템 프로그램을 선택하면 debug 불가

3 Authorization group \(권한 그룹\)

* 프로그램 실행/수정과 관련된 권한 그룹 할당. 보안 관련 프로그램이면 권한 그룹 세팅 필요

4 Logical database: type-1인 경우만 선택

* LDB를 사용해 프로그램을 구현, 사용 빈도가 높은 테이블의 데이터를 조회라기 위해 join이 자주 사용되고 ,  조회 조건이 유사한 경우를 하나의 패키지로 생성해 재사용 할 수 있도록 해주는 것이 LDB이다.

### Report program의 구조\(선언\)

3가지 구LI

1. 데이터 선언부와 조회 선택 화면 \(SELECTION SCREEN\)
2. 실행 시점까지의 Event
3. 데이터를 뿌려주는 List Event

위에 3가지 구조들의 키워드

1 프로그램 선언 

```text
REPORT pgm_id
TABLES: sflight.
DATA: l_carrid TYPE sflight-carrid.
//data 선언

SELECT-OPTION: SEL_CARR FOR sflight-CARRID.
PARAMETERs: p_carr LIKE sflight-carrid.
//selection screen
```

2 Event

```text
INITIALIZATION.
AT SELECTION-SCREEN. "(OUTPUT, ON VALUE REQUEST.)
START-OF-SELECTION.
"(SELECT * FROM ~~ 또는 GET<TABLE>~~.)
END-OF-SELECTION.
```

3 List process event

```text
TOP-OF-PAGE.
END-OF-PAGE.
AT LINE-SELECTION.
AT PF<NN>
AT USER-COMMAND.
```



### Report program의 호출 \(calling program\)

2가지 방법

* 타 프로그램 호출 후 복귀 x: SUBMIT \(TYPE1 Program 호출\) / LEAVE TO TRANSACTION\(트랜잭션 호출\)
* 타 프로그램 호출 후 복귀 O: SUBMIT AND RETURN\(TYPE1 Program 호출\) / CALL TRANSACTION \(트랜잭션 호출\)

 Type1 프로그램이 타 프로그램에서 호출될 때는 LOAD-OF-PROGRAM 이벤트 라는 것이 자동으로 수행된다. 클랫의 CONSTRUCTOR 메서드와 유사한 기능을 수행하며 리포트 프로그램에서 처음 수행되는 INITIALIZATION 이벤트 이전에 수행된다. 이것은 실행 가능한 프로그램은 소스에 SUBMIT 구문을 암묵적으로 포함하고 있다는 것을 의미한다.

```text
SUBMIT <rep> AND RETURN.

LEAVE TO TRANSATION tcod.
CALL TRANSACTION tcode.
```









