# Untitled

0714 &gt; alv 실습 패키지 ZPACKAGE\_AINALV 새로 만듦

실습1 

1. SCARR DB table 조회하는 프로그램
   1. 프로그램 생성 \(ztest\_alv1\_30\)
   2. 데이터를 담을 internal tab 생성  \(아래 코드까지가 91p가 Area만든 것\)

```text
*&---------------------------------------------------------------------*
*& Report ZTEST_ALV1_30
*&---------------------------------------------------------------------*
*&
*&---------------------------------------------------------------------*
REPORT ztest_alv1_30.

"scarr의 데이타 조회 프로그램

TABLES scarr. "db table의 구조를 갖는 str

DATA gt_itab1 TYPE TABLE OF scarr. "internal tab 생성.
DATA gs_scarr TYPE scarr. " wa

DATA gt_itab2 LIKE TABLE OF gs_scarr.

DATA ok_code TYPE sy-ucomm. "field 하나

*PARAMETERS: pa_car TYPE scarr-carrid.

SELECT-OPTIONS: so_car FOR gs_scarr-carrid, "wa를 참조
                so_car2 FOR scarr-carrid. "tables로 선언한 것을 참조/ 두개 다 가능

SELECT * FROM scarr "select-option의 경우
  INTO TABLE gt_itab1 "gt_itab1이 scarr과 구조가 다르다면 into CORRESPONDING을 해줘야함
  WHERE carrid IN so_car. "select option이기 때문에 = 이 아닌 in을 줘야함

*BREAK-POINT.

*SELECT * FROM scarr   "parameter의 경우
*  INTO TABLE gt_itab1
*  WHERE carrid = pa_car.

  call screen 100.


*&---------------------------------------------------------------------*
*& Module STATUS_0100 OUTPUT
*&---------------------------------------------------------------------*
*&
*&---------------------------------------------------------------------*
"PBO생성시 include가 아닌 mainprog에 모듈을 만듦

MODULE status_0100 OUTPUT.
  SET PF-STATUS '0100'.
  SET TITLEBAR '0100'.
ENDMODULE.
*&---------------------------------------------------------------------*
*&      Module  EXIT  INPUT
*&---------------------------------------------------------------------*
*       text
*----------------------------------------------------------------------*
MODULE exit INPUT.

  CASE ok_code.
    WHEN 'BACK'.
      LEAVE TO SCREEN 0.
    WHEN 'EXIT' OR 'CANC'.
      LEAVE PROGRAM.
  ENDCASE.

ENDMODULE.
```



외부강사님 :  

* 교육과 함께 같이 하면 좋았을 것, 스스로 준비하지 못해 아쉬웠던 점: 이지아밥을 다시 보겠다. 
* 교육과정에서 이것만큼은 꼭 하고 가면 좋겠다: 써티 딸 수 있으면 따라 SD/MM , FIORI=&gt; 따기 / 아밥 더 열심히 하기 &gt; fi준비하기 
  * SI: 프로젝트 &gt; 자리 안 맞다..개발이 잘 맞는 것을 어필할 것,,
  * SM: 운영직 
* 교육 내용중 어려웠던 것 : 빅데이터\(빅데이터 과정이셨다.\) / 메리트 SAP 서버 접속하는 것 
* 추천 자료 : 이지 아밥 SAP PRESS에서 나오는 원어 서적 
* 아밥 제일 어려웠던 것 &gt; CLASS  \(다른 언어에도 있으니까 클래스 개념을 다른 언어로 공부해도 됨\)
* ALV EVENT와 핸들링을 할줄 알면 초급개발자면 된다. 
* 프로젝트 주제: 주제를 주도적으로 정할 것 / QM모듈을 기준으로 CBO프로그램만드는 것을 하셨는데 -&gt; 우리는 뭘 하려나 ?
* 취업하실 때 준비하신 것 없음 &gt; 워드 1급 있으심,
* 초봉 아밥 개발자 2천 중후반~으로 시작 3년 이후 연봉 4000안되면 나가리
* 현재 현대 SI프로젝트 시작, 오뚜기 신규 구축 
* 다니고 있는 회사 선택한 이유: 뽑혀 ,, ,, 나이가 많았다. ㄹ후러러럴ㄹ, ,,잘가자~
* 프로젝트: ,,,,무임승차 없을 수 없다리~ 아자아자 연연하지말자
* 프로젝트가 현업에 도움이 됐던 점: 현장에 가서 비교하면서 틀린게 뭔지 알 수 있었다.
* 취업에 대해 궁금한 점 : 교육 끝나고 두달 되고 하셨음 \(자소서보다 포트폴리오를 준비하는게 더 좋다.\)
* 포트폴리오 구성: 각자 다르겠지만 만든 화면\(프로세스가\)이 어떻게 굴러가는지에 대한 것을 말하는게 더 좋다. 어떤거에 집중을 많이 했었는지\(에러 핸들리 같은 것을 어떻게 신경썻는지 잘 말하셨다고 함\) PPT에 내용을  그냥 써도됨
* 아밥만 하셨음 SI에 가고 싶었지만 PP모듈에서 하고 계신다. 
* 앞으로의 계획 \(강사님의\): 3년차에 연봉이 안맞으면 나갈예정~SI를 보내달라하겠지만 ,,,
* 비즈니스 로직을 신경써서 프로그래밍을 모르는 컨설턴트가 봐도 알 수 있게 쉽게 해야함 , 절차적으로 쉽게 예를 들어서 OOP로 자바 연결해서 쓰며 안됨,,,, 레퍼런스 체크할 때 불리함 퍼포먼스 튜닝은 잘 하지 않음 







