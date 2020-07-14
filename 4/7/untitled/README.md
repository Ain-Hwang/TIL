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
  * SI: 프로젝트 SM: 운영직 
* 교육 내용중 어려웠던 것 : 빅데이터\(빅데이터 과정이셨다.\) / 메리트 SAP 서버 접속하는 것 
* 추천 자료 : 이지 아밥 SAP PRESS에서 나오는 원어 서적 
* 아밥 제일 어려웠던 것 &gt; CLASS  \(다른 언어에도 있으니까 클래스 개념을 다른 언어로 공부해도 됨\)
* ALV EVENT와 핸들링을 할줄 알면 초급개발자면 된다. 
* 프로젝트 주제: 주제를 주도적으로 정할 것 / QM모듈을 기준으로 CBO프로그램만드는 것을 하셨는데 -&gt; 우리는 뭘 하려나 ?
* 취업하실 때 준비하신 것 없음 &gt; 워드 1급 있으심,
* 초봉 아밥 개발자 2천 중후반~으로 시작 
* 






