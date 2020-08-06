# 0806

&lt;BDC&gt;

* 레코딩이 용이한 tcode를 찾아야함
* 엑셀에도 메크로 기록 기능이 있는데 작업을 하면 메크로 기능으로 작업마다 그 기능을 입력하게 됨 이것과 비슷하게 BDC도 화면에 대한 모든 기록 로그를 남기게 됨 

-자재생성 mm01 / T-CODE: CLSAP30\_MM001 

자재를 하나 만듦 \( 보통 mm 모듈하는 사람들만 자재생성을 함 \)

![](../../../.gitbook/assets/image%20%28231%29.png)

![](../../../.gitbook/assets/image%20%28244%29.png)

이제 레코딩을 뜰거임 TCODE = SHDB

![](../../../.gitbook/assets/image%20%28241%29.png)

NEW를 눌러서 RECODING을 생성해줌 MM01\_30\_1으로 그리고 TCODE에 MM01\(자재생성\) 입력 START 버튼을 누름 시간이 아니라 뭘클리하고 입력했는지는 지를 받음 그러면 MM01로 이동함그래서 자재를 생성하면

![](../../../.gitbook/assets/image%20%28238%29.png)

이런 레코딩화면을 볼 수 있음 커서를 지우고 싶어서 커서에 커서를 놓고 빼기를 누르면 빠짐

![](../../../.gitbook/assets/image%20%28233%29.png)

이걸 더블 클릭하면 

![](../../../.gitbook/assets/image%20%28232%29.png)

해당하는 작업이 있던 곳으로 이동함 

![](../../../.gitbook/assets/image%20%28239%29.png)

/커서와  SUBSCR을 삭제하고 필요한 것만 남긴 뒤 저장

![](../../../.gitbook/assets/image%20%28235%29.png)

다시 SHDB 로 가서 내껄 검색하면 레코딩이 있는걸 볼 수 있음 들어가서

![](../../../.gitbook/assets/image%20%28243%29.png)

자재 코드를 바꿔서 똑같이 생성할 수 있음 수정 버튼&gt; 자재 코드 바꾸고 &gt; PROCESS버

![](../../../.gitbook/assets/image%20%28234%29.png)

레코드 순서대로 똑같이 흘러가는 것을 볼 수 있

![](../../../.gitbook/assets/image%20%28242%29.png)

새 프로그램을 하나 생성해주고 BAPI 샘플에서 MAIN만 긁어옴 그리고 CALL TRANSATION을 용할 거임 키워드에 커서를 두로 F1을 누르면 구문에 대한 설명을 볼 수 있

```text
CALL TRANSACTION 'MM01' USING GT_BDC "MM01이라는 티코드를 GT_BDC를 갖고 호출해라~
      OPTIONS FROM gs_opt
      MESSAGES INTO GT_MSG. "PROCESS가 진행되면서 뿌려줄 메세지
       "처리 결과를 받아야함 BAPI는 RETURN으로 받았지만 이거는 따로 메세지 구문이 있음 F1 KEY로 볼 수 있음       
```

![](../../../.gitbook/assets/image%20%28230%29.png)



