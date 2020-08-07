# 0807

&lt;마지막 시간 템플릿 좀 더 만들기&gt;

&lt;docking container&gt;

![](../../../.gitbook/assets/image%20%28280%29.png)

dock\_at\_left로 주었을 때 

![](../../../.gitbook/assets/image%20%28279%29.png)

extension은 그냥 큰 수를 주면 됨. 2000정도 그럼 거의 풀스크린  &gt;&gt;cl\_gui\_docking\_container=&gt;ws\_maximizebox 를 주는 경 우도 있음 숫자를 더 많이 사용한다고 하심



&lt;splitter container&gt;

![](../../../.gitbook/assets/image%20%28278%29.png)

![](../../../.gitbook/assets/image%20%28277%29.png)

DOCKING 을 만들고 SPLITTER로 나눔

![](../../../.gitbook/assets/image%20%28283%29.png)

스플리터 클래스에 CONTAINER 메소드의 파라미터를 보면 이렇게 돼 있음 

![](../../../.gitbook/assets/image%20%28281%29.png)

![](../../../.gitbook/assets/image%20%28276%29.png)

이렇게 들어가야

![](../../../.gitbook/assets/image%20%28282%29.png)

DOCKING을 이용해 CONTAINER를 만들고 그걸 SPLITTER로 나룸 나눠진 각각의 CONTAINER에 ALV를 얹어준다.

![](../../../.gitbook/assets/image%20%28274%29.png)



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

&lt;취업 관련&gt;

* 계속 사이트 보고,,, 스펙관련해서 준비하기
* 3기 취업률
* 설명
  * 자격증, 학점 기본 소양 큰비중은 아님 옵션
  * SKILL : 단기기술 &gt;&gt; 현재 하고 있는 것 개발에 대한 기술 &gt;&gt; 아밥 열심히~~해라!
  * 줄석률 80퍼를 채운 시점에서 공고를 받게 됨 \(개인마다 다름 출석률이기 때문에\) 공고를 통해서 자소서를 매니저님께 드리거나 회사 사이트에서 직접 지원하는 것 / 자소서 첨삭 &gt; 멘토님께 드리는 것이 정확함  / 기업 공고를 수료후 9개월동안 계속 공고를 주심 &gt; 만일 들어갔다 퇴사하면 공고를 다시 주심
  * 파트너사 기업 조사하기 &gt; 필요한 스펙 알아보기 
  * 컨설턴트: 회계법인 쪽에서 주로 뽑고 &gt; 계획을 짜주는 사람이라고 생각하면  쉽다!!!~~





=====================================================수업이어서

CTS = SE09 &gt; 중요한 티코드 

![](../../../.gitbook/assets/image%20%28285%29.png)

WORKBENCH &gt; 개발자 / CUSTOMIZIONG &gt;  컨설

 MODIFIABLE &gt; 수정가능한 모드냐 / RELEASED &gt; 완료된 모드냐 



가 주로 사용 \(현업  = 내가 만든 프로그램을 쓰는 사람 / 만드는 사람 SYSTEM을 구성하는 사람은 \(개발, SM\) 현업이라 하지 않음\)

CTS라 함은 현재 개발에서 운영으로 



#### batch job 

 SE36에서 등록하고 

SM37 &gt;  백그라운드로 돌아가는 프로그램 즉 눈으로 확인하지 않고 서버에서 그냥 돌리는 프로그램,  정기적인것도 있고 아닌 것도 있음 &gt; 유지보수하는 사람들이 자주 사용 

인터페이스 = SAP에서는 RFC, MESSAGE SERVER 같은 것을 말한다 \(SYSTEM같에 데이터를 주고 받는 것\) FUNCTION그룹에서 REMOTE-FUNCTION  MODULE을 찍어두면 RFC 가 가능  &gt; FUNCTION을 파라미터가 대표적인 인터페이스  / 인터페이스 중간에 PAI\(pi\)와 EAI같은게 많이 등자 &gt; 이것도 RFC처럼 타시스템과 연결해주는 것 웹서비스 방식일 경우는 RFC와 다름 ;

#### DBI

SAP DB에는 아무거나 종류가 다양하게 올 수 있음  dbi가 있기 때문에 / 아예 다른 곳에 있는 db sap11에 있는 게 아닌 다른 곳에 있는 db도 다이렉트 접근이 가능 문법은 open sql말고 해야하긴 함. / 다른 곳에서 sap  db도 접근하려고 하면 절대 안됨.  



