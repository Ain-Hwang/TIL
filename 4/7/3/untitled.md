# 0730

실습 이어서 

1. alv에 itab에 있는 정보를 스크린에 alv에 뿌려준다. 

   \(itab과 alv의 값은 동시적용이 아니다 한번뿌려주면 끝 만약 값을 바꾸고 싶으면 itab의 정보를 먼저 바꾸고 alv를 refresh해줘야함  append로 넣고\)

![](../../../.gitbook/assets/image%20%28200%29.png)

200에서 save 가 들어오면 gs\_200의 값을 zt30\_0010\_1 즉 db tab에 넣어라. 

![](../../../.gitbook/assets/image%20%28197%29.png)

새 값을 db에서 불러와서 다시 alv에 뿌리기 위해서 refresh를 해주는데 go\_cont가 initial이 아닐경우 한다.

![](../../../.gitbook/assets/image%20%28191%29.png)

PERFORM get\_taxt\_single\_line CHANGING wa.



![](../../../.gitbook/assets/image%20%28189%29.png)

message class 추가

![](../../../.gitbook/assets/image%20%28190%29.png)

첫번째 메세지 추가

![](../../../.gitbook/assets/image%20%28195%29.png)

i\_\_\_는 팝업으로  s\_\_\_는 왼쪽 하단바에 성공타입 메시지 display like하면 실제 그 타입은 아니지만 그런 타입으로 



====================================================================================

&lt;변경버튼&gt;

"만약에 지울 수 없는 수정할 수 없는 문서 같은 것\(자재전표 같은 것\)1000원으로 잘 못 끊어도 데이타를 지우는게 아니라 -1000원을 줘야함 "삭제 플래그가 남도록 CBO TAB은 괜찮은데 STANDARD TAB은 안됨.

![](../../../.gitbook/assets/image%20%28198%29.png)

SE37에서 POPUP\_TO\_CONFIRM  FUNCTION을 살펴보자. FUNCTION은 그 안에서 F8을 누르면 바로 실행가능 

![](../../../.gitbook/assets/image%20%28193%29.png)

파라미터를 넣어두고 테스트를 충분히 해두고 사용하는 것이 좋다 X는 옵션 값을 넣지 않아도 됨.

![](../../../.gitbook/assets/image%20%28199%29.png)

이런 값들을 넣어 주고 F8로 실행하면 

![](../../../.gitbook/assets/image%20%28188%29.png)

이런 결과가 나오는 구나~ 이런걸 확인 해야함 또 저렇게 버튼이 있다면 눌러 보고 

![](../../../.gitbook/assets/image%20%28196%29.png)

YES를 누르면 ANSWER에 결과가 1이 나오고 

![](../../../.gitbook/assets/image%20%28194%29.png)

NO를 누르면 2가 나온다 이런 걸 갖고 그 결과 값에 따라서 후속 처리를 하는 코딩을 해줄 것

 변경처리에 대한 POPUP 반드시 만들어 주자 실무에서도!!







