# Class

## 1. Global / Local class

abap object에서 클래스는 전역, 지역 변수로 선언할 수 있다. \(t-code: se24\) class builder를 이용해 전역 클래스와 전역 인터페이스를 정의한다, 이렇게 정의된 클래스들은 class pool에 저장되며 모든 abap 프로그램은 전역 클래스에 접근해 사용할 수 있다. 지역 클래스와 지역 인터페이스는 프로그램 내에서 선언되며, 자신이 정의된 프로그램에서만 사용할 수 있다. 시스템은 먼저 프로그램 내부의 정의된 지역 클래스를 탐색하고 존재하지 않으면 전역 클래스를 찾게 된다. abap프로그램 내에서 사용될 때는 전역 클래스와 지역 클래스 간에는 아무런 차이가 없다. 

```text
CLASS c1 DEFINITION.
    PUBLIC SECTION.
    METHODS meth.
ENDCLASS. "c1 class 정의

CLASS c1 IMPLEMENTATION.
    METHOD meth.
        WRITE / 'CLASS TEST'..
    ENDMETHOD.
ENDCLASS. "c1 class 구현

DATA: go_cref TYPE REF TO c1. 

START-OF-SELECTION.
    CREATE OBJECT go_cref.
    CALL METHOD go_cref->meth.
```

## 2. Class 구성 요소

클래스의 모든 요소는 선언부에서 선언된다. 구성 요소들은 클래스 내에서 객체의 속성을 정의한다. 클래스를 저의할 때 각 항목은 3개의 접근 제한 영역\(Visibility section\) 중 한 곳에서 선언돼야 한다. 접근 제한 영역은 클래스 간의 외부 interface를 정의한다. 클래스의 모든 항목은 클래스 내부에는 모두 보이지만 선언 방식에 따라 다른 클래스에서는 인터페이스 되지 않을 수 있다. 

#### 클래스에는 두 가지 종류의 구성 요소\(component\)가 존재한다.

* 각 클래스의 객체\(인스턴스\)마다 존재하는 구성요
  * instance-specific항목으로 instance component\(인스턴스\)라고 한다. 이것은 클래스를 참고해 객체를 생성하면 메모리에 생성되는 즉 객체를 생성할 때 마다 초기화되는 항목들이다.
* 인스턴스의 수에 상관 없이 전체 클래스에서 오직하나만 존재하는  구성요소
  * non instance-specific항목으로 static component라고 한다. 이것은 클래스 생성자\(CREATE OBJECT 구문\)를 만나면 프로그램이 종료할 때까지 메모리에 저장되며 클래스에 의존적인 항목이다. 
  * static 속성은 CLASS-DATA구문으로 선언하고 static메서드는 CLASS-METHOD 구문으로 선언한다. 
  * Static속성과 메서드는 클래스의 컴포넌트를 조작하기 위해 선언되는 것이며 객체를 생성하지 않아도 메모리에 로드되 바로 사용할 수 있다. 

#### ABAP Object에서 클래스는 다음의 항목 \(attribute, method, event\)들을 정의할 수 있다.

### 2-1. Attribute

속성\(attribute\)은 모든 abap 데이터 타입을 가질 수 있는 클래스의 내부 데이터 필드이다. 객체의 상태는 attribute의 콘텐츠에 의해 결정된다. 속성의 한 가지 종류는 Reference variable이다. Reference variable은 객체를 생성하고 주소를 지정한다. 클래스 내부에서 정의될 수 있으며 클래스 내부로부터 객체에 접근할 수 있도록 해준다.

* Instance Attribute: 인스턴스 속성의  콘텐츠는 instance-specific 객체의 상태를 정의한다. 클래스 내에서 data 구문을 사용해서 인스턴스를 선언할 수 있다.

```text
DATA l_data TYPE c.
```

* Static Attribute: static 속성의 콘텐츠는 클래스의 모든 인스턴스에 유용한 클래스의 상태를 정의한다. 즉 인스턴스 수에 상관없이 클래스에 의존적이며 클래스만의 고유한 영역이다. CLASS-DATA구문을 이용해 선언한다. 클래스의 실행 환경에서 접근할 수 있다.

```text
CLASS-DATA c_data TYPE i.
```

### 

### 2-2. Method

메서드는 객체의 행위를 정의하는 클래스의 내부 수행 절차를 정의한다. 메서드는 클래스의 모든 속성에 접근할 수 있으며 메서드를 통해 객체의 내용을 변경할 수 있다. 

또한 파라미터 인터페이스를 제공해 사용자가 값을 가지고 객체를 호출하고 호출 후 값을 되돌려 받을 수 있도록 한다. 이러한 점에서 Function Module과 유사한 점이 있다고 할 수 있다.

클래스의 PRIVATE속성은 동일한 클래스의 메서드에 의해서만 변경할 수 있다. 클래스 정의\(DEFINITION\) 부분에서 METHOD구문을 이용해 정의하고 IMPLEMENT 부분에서 메서드 기능을 서술한다.

* instance method: methods 구문을 이용해 인스턴스 메서드를 선언한다, 클래스의 모든 속성에 접근할 수 있고, 클래스의 모든 이벤트에서 메서드를 호출할 수 있다.
* static method: CLASS-METHODS 구문을 이용해 static메서드를 선언, static 속성에 접근할 수 있고, static이벤트를 호출할 수 있다.

### 2-3. Event

이벤트는 상속 관계에 있지 않은 클래스 간에 메서드를 상호 호출해 영향을 미칠 수 있는 특별한 메서드이다. 객체\(또는 클래스\)는 다른 객체\(또는 클래스\)의 이벤트 핸들러 메서드를 호출\(trigger\)하기 위해 이벤트를 사용한다. \(이벤트 핸들러 메서드는 메서드의 한 종류이다.\) 

CALL METHOD 구문을 통해 일반 메서드르 호출하느 경우, 하나의 메서드는 수 많은 객체에 의해 호출될 수 있다. 이와 유사하게 모든 객체가 이벤트 메서드를 호출할 수 있으며 이벤트의 소유주인 객체만이 이벤트를 실행할 수 있다. 

일반 메서드를 호출하는 경우 호출한 프로그램이 호출하고자 하는 메서드를 결정지을 수 있다. 이와 같이 이벤트에서는 핸들러가 반응하고자 하는 이벤트를 결정할 수 있다. 클래스의 이벤트는 RAISE EVENT 구문을 사용하는 같은 클래스의 메서드를 호출하게 된다. 다른 클래스의 이벤트를 호출할 때는 FOR EVENT evt OF class 구문을 사용한다. 

* 이벤트 선언

```text
EVENT evt EXPORTING...VALUE(e1 e2 .) TYPE type [optional]..

```

* 이벤트 호출

```text
RAISE EVENT evt EXPORTING e1 = f1 e2 = f2...
```

* Event handler method 선언

```text
METHODS meth FOR EVENT evt OF cif IMPORTING e1 e2...
```

* Event handler method 등록

```text
SET HANDLER h1 h2.... [FOR]....
```

### 2-4. Visibility Section \(접근 제한 영역\)

* public section: 클래스에서 public section으로 선언된 컴포넌트들은 모든 클래스에서 접근할 수 있다. public 클래스의 컴포넌트\(=멤버, 항목\)들은 클래스와 사용자 사이에 인터페이스를 구성한다.
* protected section: protected로 선언된 항목은 자신과 상속 받은 클래스에서만 접근할 수 있고 자식과의 인터페이스 역할을 담당
* private section: private로 선언된 컴포넌트는 같은 클래스의 메서드에서만 보인다 외부에서 접근할 수 없으며 완전히 클래스 내부에서 캡슐화돼 있다, 클래스 implementation 파트의 모든 메서드는 클래스 내에서 접근 제한 없이 사용할 수 있다.

\*캡슐화\(encapsulation\): 캡슐화의 기본 목적은 객체 내부의 데이터는 그 객체가 가진 메서드를 통해서만 사용 및 변경할 수 있도록 하고, 다른 객체에는 내부 구조를 은폐시키는 것이다. 내부 구조를 숨김으로써 객체의 모습을 단순화해 객체의 구성을 알지 못해도 쉽게 사용할 수 있도록 해준다.

## 3. Object

### 1.  Object Reference 

ABAP 프로그램에서 객체에 접근하려면 객체 참조를 사용해야 한다 객체 참조는 객체에 대한 포인터로 정의된다. ABAP에서 객체 참조는 항상 객체 참조 변수 내에 존재하게 된다. 

#### Object Reference Variable\(객체 참조 변수\)

abap에는 reference를 포함할 수 있는 두 가지 타입의 변수가 존재한다. 그것은 객체 참조 변수와 데이터 참조 변수 \(data reference variable\)이다.  

```text
DATA cref TYPE REF TO class "Object Reference Variable 구
```

\(객체 참조 변수 생성하는 모습 / cref = 객체 참조 변 \)객체 참조 변수는 이미 존재하는 객체를 참고하거나 초기화할 수 있다. 객체를 가리키는 참조 변수가 객체의 실체를 알고 있으며 클래스의 인스턴스는 객체를 가리키는 참조 변수를 사용해 주소를 지정할 수 있다. 

객체 참조 변수를 이용하는 객체들은 객체의 구성요소에 직접 접근할 수가 없으며 reference\(객체의 주소\)를 이용해야 한다.

abap standard type처럼 참조 변수를 위해  이미 정의된 데이타 타입이 존재 class reference와 interface reference 두가지 객체 참조 타입이 존재 모든 변수와 마찬가지로 객체 참조 변수를 clear 구문으로 초기화할 수 있다. 객체 참조 변수의 초깃값은 객체가 참고하 데이터 타입과 연결되지는 않는다.

### 2. Object 생성

객체 참조 변수를  생성하고 그 것을 이용해 클래스의 인스턴스인 객체를 생성하게 된다. 객체 참조 변수가 프로그램 선언부에서 이미 객체를참조하고 있다면, 인스턴스 생성 시 다시 type 구문을 사용할 필요가 업다. 

```text
CREATE OBJECT cref. "프로그램 선언부에 객체를 참조하고 있을 때 

or

DATA: l_ref TYPE REF TO OBJECT. 
CREATE OBJECT l_ref TYPE  class. 
```

예외적으로 DATA: l\_ref TYPE REF TO OBJECT. 구문과 같이 최상위 클래스인 OBJECT를 참조하는 참조 변수 l\_ref를 생성하였다면 인스턴스 생성 시 CREATE OBJECT l\_ref TYPE  class. 와 같이 선언해야 한다. 

### 3. Object Component 접근

**객체의 속성과 메서드에 접근**하기 위해 ref-&gt;attr 또는 ref-&gt;meth 구문을 사용한다. ref-&gt;meth 구문은  CALL METHOD ref-&gt;meth의 축약형이다.

**객체가 생성되기 이전에 클래스의 static 컴포넌트에 접근**할 수도 있다. static 속성에 접근하려면 class=&gt;attr 구문을 사용하고 static 메서드는 CALL METHOD class=&gt;meth 구문을 이용한다. 

### 4. 클랫에서 하나 이상의 인스턴스 생성

CREATE OBJECT 구문을 이용해 새로운 객체를 생성할 수 있다. 프로그램 내에서 같은 클래스로 부터 무한한 객체를 생성할 수 있으며, 객체들은 서로 완전히 독립적으로 행동하며 프로그램 내에서 각자의 이름과 속성을 갖는다.

### 4.1 객체 참조 할당

MOVE 구문을 이용해 다른 참조 변수에 reference를 할당할 수 있다. 같은 객체에 연결된 객체 참조 변수 내에 reference를 생성할 수 있다. MOVE 구문을 사용하거나 할당 기호 \(=\)를 사용할 때 시스템은 할당할 수 있는 타입인지를 자동으로 체크한다. 

```text
cref1 = cref2 MOVE
or 
cref2 TO cref1
```

dnl rnansdmf

위 구문을 사용하려면 두 개의 클래스 \(cref1, cref2\)는 같은 타입이어야한다. 즉 같은 클래스를 참고해야한다는 의미이다. 

### 4.2 CASTING

casting 기호\(?\)를 이용해 서로 다른 클래스에서 파생된 객체를 참고해 또 다른 객체를 생성할 수 있다. 이때 다른 클래스는 부모 클래스와 부모 클래스를 상속 받은 자식 클래스등과 같이 다른 타입을 의미한다. 자식 클래스는 부모가 가진 속성과 메서드를 재정의하거나 추가할 수 있다. 부모에서 파생된 객체와 자식에서 파생된 객체 타입은 같지 않더라도 이때는 casting 기호 \(?\)를 이용해 구문 에러 없이 프로그램을 실행시킬 수 있다.

## 4. Method 

### 1. method선언

instance method를 선언하려면 다음 구문을 사용

```text
METHODS meth IMPORTING [VALUE(] i1 i2 ...[)] TYPE type [OPTIONAL].
             EXPORTING [VALUE(] e1 e2 ...[)] TYPE type.
             CHANGING [VALUE(] c1 c2 ...[)] TYPE type [OPTIONAL].
                RETURNING VALUE(r)
                EXCEPTIONS exc1 exc2...
```

static method를 선언하려면 다음과 같이 선언한다.

```text
CLASS-METHODS meth...
```

method를 선언할 때 IMPORTING, EXPORTING, CHANGING, RETURNING을 이용해 파라미터 인터페이스를 정의할 수 있다. 인터페이스 파라미터의 속성을 정의하며, 파라미터의 참조 주소\(reference\)와 값\(value\)을 선택하여 사용할 수 있다. Function module이 EXPORT / IMPORT/CHANGING 매개 변수를 주고 받는 것과 같이, 클래스 메서드에서는 EXPORTING/IMPORTING/CHANGING 구문을 사용한다. 

값을 매개변수로 넘겨 주려면 VALUE 구문을 선언해야 한다. RETURN VALUE는 항상 값으로 반환된다. 함수 모듈에서와 같이 예외처리 시에 EXCEPTIONS를 사용할 수 있다. 

### 2. Method 구현 

* 클래스에서 선언된 메서드를 implementation 파트에서 선언하고 기능을 구현해야한다. \(implementation 또는 implement라는 것은 메서드의 기능을 구현하는 것을 의미한다.\) 
* 클래스의 메서드 선언 부분에 정의 된것 이외의 인터페이스 파라미터를 정의할 필요없다.
* Function Module 과 같이  raise exception과 

