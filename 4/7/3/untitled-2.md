# 0806

&lt;BDC&gt;

* 레코딩이 용이한 tcode를 찾아야함
* 엑셀에도 메크로 기록 기능이 있는데 작업을 하면 메크로 기능으로 작업마다 그 기능을 입력하게 됨 이것과 비슷하게 BDC도 화면에 대한 모든 기록 로그를 남기게 됨 

-자재생성 mm01 / T-CODE: CLSAP30\_MM001 

자재를 하나 만듦 \( 보통 mm 모듈하는 사람들만 자재생성을 함 \)

![](../../../.gitbook/assets/image%20%28232%29.png)

![](../../../.gitbook/assets/image%20%28268%29.png)

이제 레코딩을 뜰거임 TCODE = SHDB

![](../../../.gitbook/assets/image%20%28261%29.png)

NEW를 눌러서 RECODING을 생성해줌 MM01\_30\_1으로 그리고 TCODE에 MM01\(자재생성\) 입력 START 버튼을 누름 시간이 아니라 뭘클리하고 입력했는지는 지를 받음 그러면 MM01로 이동함그래서 자재를 생성하면

![](../../../.gitbook/assets/image%20%28251%29.png)

이런 레코딩화면을 볼 수 있음 커서를 지우고 싶어서 커서에 커서를 놓고 빼기를 누르면 빠짐

![](../../../.gitbook/assets/image%20%28234%29.png)

이걸 더블 클릭하면 

![](../../../.gitbook/assets/image%20%28233%29.png)

해당하는 작업이 있던 곳으로 이동함 

![](../../../.gitbook/assets/image%20%28252%29.png)

/커서와  SUBSCR을 삭제하고 필요한 것만 남긴 뒤 저장

![](../../../.gitbook/assets/image%20%28239%29.png)

다시 SHDB 로 가서 내껄 검색하면 레코딩이 있는걸 볼 수 있음 들어가서

![](../../../.gitbook/assets/image%20%28267%29.png)

자재 코드를 바꿔서 똑같이 생성할 수 있음 수정 버튼&gt; 자재 코드 바꾸고 &gt; PROCESS버

![](../../../.gitbook/assets/image%20%28236%29.png)

레코드 순서대로 똑같이 흘러가는 것을 볼 수 있

![](../../../.gitbook/assets/image%20%28264%29.png)

새 프로그램을 하나 생성해주고 BAPI 샘플에서 MAIN만 긁어옴 그리고 CALL TRANSATION을 용할 거임 키워드에 커서를 두로 F1을 누르면 구문에 대한 설명을 볼 수 있

```text
CALL TRANSACTION 'MM01' USING GT_BDC "MM01이라는 티코드를 GT_BDC를 갖고 호출해라~
      OPTIONS FROM gs_opt
      MESSAGES INTO GT_MSG. "PROCESS가 진행되면서 뿌려줄 메세지
       "처리 결과를 받아야함 BAPI는 RETURN으로 받았지만 이거는 따로 메세지 구문이 있음 F1 KEY로 볼 수 있음       
```

![](../../../.gitbook/assets/image%20%28231%29.png)





![](../../../.gitbook/assets/image%20%28253%29.png)

![](../../../.gitbook/assets/image%20%28240%29.png)

![](../../../.gitbook/assets/image%20%28238%29.png)

![](../../../.gitbook/assets/image%20%28265%29.png)

레코드의 정보를 다 코드로 작성

이렇게 레코드 정보대로 다 입력하고 프로그램 실행하면 

![](../../../.gitbook/assets/image%20%28246%29.png)

새로운 자재이름과 내역을 입력하고 

![](../../../.gitbook/assets/image%20%28254%29.png)

레코드를 돈다 이렇게 과정을 하나하나 보여주는게 A모드고 N모드는 백그라운드로 진행화면 없이 실행한다 E모드는 N과 같이 진행하지만 에러가 나면 보여줌

![](../../../.gitbook/assets/image%20%28255%29.png)

여기서 새로운 자재생성이 완료됨.

![](../../../.gitbook/assets/image%20%28235%29.png)

이렇게 CALL TRANSACTION을 줄 때 

![](../../../.gitbook/assets/image%20%28262%29.png)

F1으로 해당하는 구문에 필요한 ITAB이나 MODE OPTION에 대한 TYPE들을 확인하고 TOP에서 미리 선언해 둬야함 

![](../../../.gitbook/assets/image%20%28256%29.png)

이렇게 

![](../../../.gitbook/assets/image%20%28260%29.png)

그리고 호출할 때 선언한 타입으로 써줌 그러면!!! 선언한 TYPE을 보기 위해서 직접 보자 

![](../../../.gitbook/assets/image%20%28241%29.png)

![](../../../.gitbook/assets/image%20%28242%29.png)

SHDB 에서 RECODE를 확인하면 이런 필드의 테이블 형태로 돼 있는 것을 확인할 수 있음 / 레코드의 로그? 와 같은 걸 만들고 싶다면 각각의 FIELD에 들어와 있는 로그값들을 입력해 주면 됨.

&gt;&gt;&gt;즉 GT\_DBC의 모양과 이 레코드화면의 형태가 같다.!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 

```text
 "첫번째 레코드 스크린에서 가져온 것
  CLEAR: gt_bdc.
  CLEAR: gs_bdc.

  gs_bdc-program = 'SAPLMGMM'.
  gs_bdc-dynpro = '0060'.
  gs_bdc-dynbegin = 'X'.
  APPEND gs_bdc TO gt_bdc.

  CLEAR: gs_bdc.
  gs_bdc-fnam = 'BDC_OKCODE'.
  gs_bdc-fval = '=ENTR'.
  APPEND gs_bdc TO gt_bdc.

  CLEAR: gs_bdc.
  gs_bdc-fnam = 'RMMG1-MATNR'.
  gs_bdc-fval = p_matnr.
  APPEND gs_bdc TO gt_bdc.


  CLEAR: gs_bdc.
  gs_bdc-fnam = 'RMMG1-MBRSH'.
  gs_bdc-fval = 'M'.
  APPEND gs_bdc TO gt_bdc.

  CLEAR: gs_bdc.
  gs_bdc-fnam = 'RMMG1-MTART'.
  gs_bdc-fval = 'FERT'.
  APPEND gs_bdc TO gt_bdc.


  "두번째 레코드 스크린에서 가져온 것
  CLEAR: gs_bdc.

  gs_bdc-program = 'SAPLMGMM'.
  gs_bdc-dynpro = '0070'.
  gs_bdc-dynbegin = 'X'.
  APPEND gs_bdc TO gt_bdc.

  CLEAR: gs_bdc.
  gs_bdc-fnam = 'BDC_OKCODE'.
  gs_bdc-fval = '=ENTR'.
  APPEND gs_bdc TO gt_bdc.

  CLEAR: gs_bdc.
  gs_bdc-fnam = 'MSICHTAUSW-KZSEL(01)'.
  gs_bdc-fval = 'X'.
  APPEND gs_bdc TO gt_bdc.


  "세번째 레코드 스크린에서 가져온 것
  CLEAR: gs_bdc.

  gs_bdc-program = 'SAPLMGMM'.
  gs_bdc-dynpro = '4004'.
  gs_bdc-dynbegin = 'X'.
  APPEND gs_bdc TO gt_bdc.

  CLEAR: gs_bdc.
  gs_bdc-fnam = 'BDC_OKCODE'.
  gs_bdc-fval = '=BU'.
  APPEND gs_bdc TO gt_bdc.


  CLEAR: gs_bdc.
  gs_bdc-fnam = 'MAKT-MAKTX'.
  gs_bdc-fval = p_maktx.

  APPEND gs_bdc TO gt_bdc.


  CLEAR: gs_bdc.
  gs_bdc-fnam = 'MARA-MEINS'.
  gs_bdc-fval = 'EA'.
  APPEND gs_bdc TO gt_bdc.



  CLEAR gs_opt.
  gs_opt-dismode = 'A'. "N,E MODE가 각각
  gs_opt-updmode = 'S'.

  CALL TRANSACTION 'MM01' USING gt_bdc "MM01이라는 티코드를 GT_BDC를 갖고 호출해라~
        OPTIONS FROM gs_opt
        "처리 결과를 받아야함 BAPI는 RETURN으로 받았지만 이거는 따로 메세지 구문이 있음 F1 KEY로 볼 수 있음
        MESSAGES INTO gt_msg. "PROCESS가 진행되면서 뿌려줄 메세지

```

그게 이 코드 

만일 한과정? 로그? 작업? 을 추가 하고 싶다면 

![](../../../.gitbook/assets/image%20%28230%29.png)

추가하고 싶은 작업에 사용되는 필드를 코드에 추가하면됨 꼭 레코드랑 같지 않아도 레코드를 틀로 참고하고 하나씩 추가해도 무관함.

![](../../../.gitbook/assets/image%20%28250%29.png)

여기에 들어갈 수 있는 값중에 넣고 싶은 값을 선택해서 

![](../../../.gitbook/assets/image%20%28245%29.png)

이렇게 추가하면 이거까지 포함된 과정으로 자재를 생성함. &gt;이렇게 일일이 노가다임 

![](../../../.gitbook/assets/image%20%28263%29.png)

구문을 이렇게 추릴 수도 있음

![](../../../.gitbook/assets/image%20%28237%29.png)

퍼폼에 파라미터를 다 주고 

![](../../../.gitbook/assets/image%20%28249%29.png)

똑같이 생성됨



![](../../../.gitbook/assets/image%20%28266%29.png)

![](../../../.gitbook/assets/image%20%28247%29.png)

![](../../../.gitbook/assets/image%20%28259%29.png)

이렇게 띄워도 되지만. &gt;&gt;&gt; BAPI는 타입이 E로 딱 있는데 BDC는 MSGNR \(메세지 번호\)가 따로 있어서 그걸로 성공실패를 따져보는게 좋음 

![](../../../.gitbook/assets/image%20%28244%29.png)

이런식으로  

**&lt;bapi 구매오더변경, bdc로 자재생성 해봤다&gt;**





