# ABAP Dictionary

## ABAP Dictionary의 기능 \(t-code: se11\)

* Type Definitions \(type objects\) : Global data type에 대한 정의를 한다. 틀\(data type\) 
  * data type은 그릇\(data object\)을 만드는 틀이다.
  * Structure : type을 갖는 component들로 구성되어 있다.
  * Data Element : element type과 reference type이 존 , 필드와 같은 모습으로 기술적인 정보를 
  * Table type: internal table의 기능적 속성을 저으이하는 데  사용된다. 특별한 형태인 range table type이 존재. \*Structure의 component\(field\) 하나가 structure구조를 가질 수 있고, table 구조를 가질 수도 있다.
* Data Object  : 그릇\(data object\)이다 , 대표적으로  Table and View가 있다.  ...TYPE dbtab  / ...TYPE dbtab-comp
  * Data object는 data type을 이용해서 만드는 데이타를 담을 수 있는 그릇이다.
  * ABAP Dic에서 테이블 타입의 data object를 정의를 하면 물리적인 DB가 생성된다 .
  * \*dic에서 table이나 view에 대한 정의를 하면 물리적인 db에 반영이된다. 추가적인 index도 반영이 가능
* Service \(ABAP Tools\)
  * Input help: F4 Help를 제공, input field에 넣을 수 있는 possible value\(or possible entry라고도 함\)를 알려주는 기능
  * Field help: F1 Help를 제공, field에 대한 기술적 속성을 알려줌 
  * Input Check: Input 동작 시 폴인키에 대해서도 반영 돼 input check가 들어가다.
  * Set and release locks: lock을 set, release하려면 dic에  lock object를 생성해야함.
* Type Groups
  * Abap Dic에서 type들을 grounp 지어 놓은 것도 있음 =&gt; 대표적인 type grounp : ICON

개발 시 ABAP Tool에서 Runtime 시 ABAP / Screen Interpreter에서 또 DatabaseInterFace에서도 ABAP DIC 참조 한다.



## Type Objects

ABAP Dictionary의  type은 모든 프로그램에서 data type으로 선언해 사용 가능

### Data Type

#### 1.Data Elemants 

field type의 data type으로 의미적인 속성을 갖는다. element를 만들 때 element의 기술적인 속성을 갖는 domain이 꼭 필요한다. \(element : domain = n : 1의 관계\)

#### 특

1. 같은 field ID에 대해 여러개를 갖는다 \(다국어지원\) // Documentation \(설명서\) 데이터 요소의 내용을 설명하는 텍스트를 만들 수 있다. input field 옆에 text label,  F1 help를 갖는다.
2. 특정 Search help를 지정가능 // F4 help지정가능 
3. SET/GET parameters 지정가능 // 사용자가 입력한 값을 동일한 data element를 사용하는 input field에 후속 화면에 존재하면 parameter로 값을 읽고 screen file에 입력하는 기능을 사용할 수 있다. 각 세션의 값을 보유하기 때문이다, 로그오프 하면 값이 사라짐



#### 2. Structures

\(flat / deep str라고도 함\) Structure는 여러개의 component\(data element\(field\), View, DB table, Table type\(itab\)\)로 구성된다. 이때 모든 component가 field인 것을 **Simple structure** 라고 하고, 하나의 컴포넌트가 Table or Structure인 것은 **Nested structure**라고 한다.

#### -Simple Structure \(simple structure\)

field 단위의 component만 갖는 structure

```text
DATA wa_abr TYPE address.

wa_adr-street = 'Neurott Str. 15a'.
wa_adr-zipcode = 'p-69190'.
wa_adr-city = 'Walldorf'.
```

ABAP DIC에 있는  'address'는 'street' , 'zipcode', 'city'등의 field component를 갖고 있는 simple str type이다. 위 code는  'address'를 type으로 하는  'wa\_adr'라는 data object를 생성한 것  각각의 field로 접근 할 때 '-'를 사용해 접근할 수 있다. 

#### -Nested Structure \(deep structure\)

하나의 component가 tab or str인 structure

&lt;Component가 Structure 경우&gt;

```text
DATA wa_pers TYPR person.

wa_pers-name-firstname = 'Hans'.
wa_pers-name-lastname = 'Hans'.

wa_pers-address-street = 'Neurott Str. 15a'.
wa_pers-address-zipcode = 'p-69190'.
wa_pers-address-city = 'Walldorf'.
```

ABAP DIC에 정의 돼 있는 'person'이라는 Structure는 name과 address라는 field를 갖는데 이들은 각각 str이다. name은 first name, last name이라는 field를 갖는 str이고,  address는 street, zipcode, city라는 field를 갖는다. 이렇게 field의 field가 존재하는 것 즉, 갖고 있는 field가 str type인 것을 nested structrue라고 한다.  접근하는 법은 'str-str-field'

만약 include로 Nested str를 불러서 사용한다면 falt str\(simple\)로 사용 되기 때문에 

```text
"만약 include로 Nested str를 불러서 사용한다면 falt str(simple)로 사용 되기 때문에 

wa_pers-name-firstname = 'Hans'. "가 아닌 
wa_pers-firstname = 'Hans'. "로 쓸 수 있다.
```

&lt;Component가 Table인 경우&gt; 

```text
DATA wa_pers TYPE person.
DATA wa_tel LIKE OF wa_pers-telephone.

wa_pers-name-firstname = 'Hans'.
wa_pers-name-lastname = 'Hans'.

wa_tel-number = '+49-6229-72727'

INSERT wa_pers INTO TABLE wa_per-telephone.
```



#### 3. Table Type

\(table type = internal table type\)

Line type의 Structure가 internal tab 구조를 이루고 구조체에 데이터가 쌓이면 internal tab이 됨.                         \*물리적 db tab이 아니면 테이블을 만들 때 str형으로 만들기 가능

Line type의 str에도 여러 component\(data element\(field\), View, DB table, Structure\)가 온다.

#### Table type 정의

* Line type: internal tab의  Line에 Structure나 data type의 속성을 정의
* Access mode: 데이타의 관리와 Access mode을 알아 낸다\(결정한다\). \(사용 가능한 access mode: standard table, hashed table, sorted table, indextable가 있고 not specified 지정하지 않을 수 있다.\)
* primary key: 기본 키 정의 및 키의 \(Unique/Non-unique/Not specified\) 같은 vlaue를 정의 \(hashed tab은 항상 unique sorted tab은 세개 다 가능\)
* secondary key\(optional\): 보조키는 hashed나 sorted tab에서 사용됨. \(Unique/Non-unique 선택가능\)



### Data Objects

Data object는 data type을 이용해서 만드는 데이타를 담을 수 있는 그릇이다. table이나 view를 말한다.

**Table**

1. Table 

\*table의 이름은 system마다 고유하다.

ABAP Table은 크게 3가지 좋류가 존재한다. Transparent table, pooled Table, Cluster Table이다.  pool, cluster는 여러개의 table을 하나로 그룹 지어 놓은 ABAP dictionary object다. 

abap table의 종류는 크게 3가지가 있다.

* transparent table
* * Transparent Table
* Pooled Table
* Cluster Table

#### **=** Transparent Table

\#table 구성하는 요소: \(transparent tab 뿐 아니\)

* Table Field
  * key fields: 라인을 구분 지을 수 있는 최소의 field단위
  * function fields: key field 이외의 다른 field
  * field는 테이블의 속성을 표현
* 한줄씩의 Line\(같은 말로 tuple, record, data\)이 있다.

\#Table field 

테이블의 속성을 표현하는 개별 구성 요소로 사워 정보라느 테이블이 존재 한다면, 사원번호 /  출신지역 / 전화번호 등과 같은 사원 정보의 속성들을 정의해서 사용할 수 있다. 이런 각각의 속성들을 테이블 필드라 한다. \(abap dictionary에서는 data object를 생성, 변경, 조회, 삭제할 수 있다.\)

* field 속성 정의 \(data type, feld length, short text\) 

  field 속성은 data element와 predefined type 두가지 방식을 이요해 지정

  * data element: 사용자가 직접 생성할 수 있는 오브젝트이며 이미 존재하는 data element를 입력하면 데이터 타입, 길이와 내역이 자동으로 지정된다. \(data element를 생성했을 때 입력했기 때문\)
  * predefined type을 사용하면 정보를 직접 입력할 수 있다. 

* Reference Field와 Reference Table 
  * 수량을 표현하는 데이터 타입 QUAN과 화폐량을 표현하는 데이터 타입 CURR는 단위를 정의하는 참조 필드를 지정하여야한다.  \(QUAN = UNIT / CURR = CUKY\) 단위 \(kg, g, ton\)에 따라 같은 100이라도 전혀 다른 데이터가 될 수 있기 때문에 반드시 단위 정보를 추가한다.

\#Transparent table은 실제 물리적인 database table에 값을 저장하는 정의 부분이다.  이 테이블의 field가  의미적인 정보\(short description\)를 담는 data element를 사용하고 data element는 반드시 기술적 정보\(field type, length\)를 담는 domain을 사용한다. \*서로 다른 data element가 같은 domain을 사용할 수 있다.\*

\#transparent table은 data를 담을 수 있고, key field를 갖는다. inital value도 갖는다. 클라이언트 정보를 의미하는 MANDT field도 갖는다. 하지만 메모리 영역을 공유하지 않기 때문에 Ref 속성을 갖지 않는다. active하면 DB에 물리적  테이블이 생긴다. \(즉, 저장속사 생긴다.\)  하지만 프로그램에서는 str로 쓰인다

\#transparent tab 생성 & 저장 시하는 세팅\(technical setting\): size category\(record size\), data class\(저장공간 구분\)를 지정, Table buffer\(table buffer를 사용할 것 인가?\),  Logging \(데이타 변경에 대해 log를 남길 것인가\)

* data class: 테이블마다의 용도 별로 DB 저장소에서 물리적인 저장 공간 구분지어 관리하는 것  dic에서 구분지어 주면 물리적 DB에서도 똑같이 저장공간을 구분지어 사용
  * Master data: 자주 변하지 않는 데이타
  * Organizational Data: 인스톨, 커스터마이징할 때 설정 \(국가키 같은 것\)
  * Transaction Data: 자주 변경하는 데이타
  * System Data:SAP system 자체에서 필요한 데이
* 












 



 

