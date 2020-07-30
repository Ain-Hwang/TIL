# 0730

실습 이어서 

1. alv에 itab에 있는 정보를 스크린에 alv에 뿌려준다. 

   \(itab과 alv의 값은 동시적용이 아니다 한번뿌려주면 끝 만약 값을 바꾸고 싶으면 itab의 정보를 먼저 바꾸고 alv를 refresh해줘야함  append로 넣고\)

![](../../../.gitbook/assets/image%20%28190%29.png)

200에서 save 가 들어오면 gs\_200의 값을 zt30\_0010\_1 즉 db tab에 넣어라. 

![](../../../.gitbook/assets/image%20%28189%29.png)

새 값을 db에서 불러와서 다시 alv에 뿌리기 위해서 refresh를 해주는데 go\_cont가 initial이 아닐경우 한다.

![](../../../.gitbook/assets/image%20%28188%29.png)

PERFORM get\_taxt\_single\_line CHANGING wa.





