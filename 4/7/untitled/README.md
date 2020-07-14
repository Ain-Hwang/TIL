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



