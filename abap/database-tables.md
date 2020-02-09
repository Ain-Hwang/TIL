# Table Change

#### Table을 Conversion할 때 일어나는 performing 

바꾸는 방법 

* Delete, recreate // 삭제하고 다시 만들기
* DB에 있는 catalog Change 하기// 카탈로그를 바꾸려면 DB에 가서 직접 바꿔야함. index tab들을 다시 만들어야됨 
* convert the table //프로세스를 이용해서 바꾼다. \(ABAP Dic에서 하는 것 시간은 오래 걸려도 완벽하게 바뀌기 때문에 이 방법을 권장.\)

#### Conversion process 

* type of structure change // 구조적 변경 유형에 따라
* database system used // 사용된 db에 따라
* whether or not data already exist in the table //테이블에 이미 데이터가 있는지에 따라

위 조건들에 따라 conversin process가 달라진다.

#### conversion process의 flow

Active version에서 char60이던게 inactive version에서 char30으로 바뀜

1. TAB lock "바꾸고자 하는 tab에 lock을 건다
2. DB tab의 name 변경하고 index tab을 삭제
3. incatice version이던 걸 active ver로 바꾸고 물리적 db와 index tab을생성해둔다.
4. 2번에서 name을 바꾼 db tab의 데이타를 만들어둔 DB tab으로 옮긴다.
5. 기존에 있던 DB tab을 삭제 데이타를 옮긴 tab의 이름을 다시 원래 쓰던 이름으로 변경 index tab의 name도 
6. lock 해제

#### conversion 시에 발생할 수 있는 error들 \(주의\)

* tablespace overflow "원래 db tab을 새로운 db tab으로 copy할 때 미리 데이타 사이즈 공간 늘려 놓기
* data loss if key reduced in size "key field의 값을 사이즈를 줄이면 데이타 손실의 위험
* invalid change of type " 속성자체를 변경한 경우 \(char를  -&gt; int로\) error

#### Enhancing tab using append structure

append structure는 sap standard tab를 수정하지 않고 field를 추가할 수 있느 기능. sap의 입장에서 customer field라고 한다. 이 str의 field들의 이름은 반드시 zz or yy로 시작해야한다. 그래야 sap에서 str를 추가해도 이름이 겹쳐 에러가 날 일이 없다. 하나의 append str은 하나의 tab에만 적용 하나의 tab에는 여러 str가 추가능하다. str이 쌓인 순서대로 있어야 하기 때문에 LCHR이나 LRAW와 같은 타입의 field가 포함된 테이블과 pooled, cluster tab도 사용할 수 없다.

#### Enhancement category 

테이블을 생성하고 활성화 하면 enhancement category를 지정해야한다. 이것은 append str과 include기능을 사용하기 위한 유형을 말한다. 이 유형을 지정해야 된다.

enhancement category의 level

1: not classified: 이 str는 category가 없다.

2: not enhanceable: 이 str은 enhancement할 수 없다.

3: enhancement and character like: enhancement할 수 있지만 char 타입을 가진 field만 확장가능







