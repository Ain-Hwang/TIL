# ABAP Basic

## Data types and Data Objects

1. Data type 
   * Standard type\(built-in\): sap에서 제공하는 기본 타입
     * complete: 자릿수가 정해진 타입 &gt; D, T, I, INT8, F, STRING, XSTRING, DECFLOAT16, DECFLOAT34 
     * Incomplete: 자릿수가 지정되지 않은 타입 &gt; C, N, X, P
   * Local type: 프로그램 내부에서 개발자가 만드는 타입 
     * types:~~~~로 지정 
   * Global type: 여러 프로그램에서 동시에 사용할 수 있게 하는 타입
     * abap dictionary에서 생성하는 타입들 data element, structure, table type
2. Data object

* 위에 data type \(그릇틀\)들을 사용해 data를 담을 수 있는 data object\(그릇\) 을 만들 수 있다

```text
DATA objectname TYPE types. "Object 선언하는 법
DATA objectname LIKE objectname. "오브젝트로 오브젝트를 만들 수 있음
```

{% file src="../.gitbook/assets/data-types.docx" %}

naming role과 단축키 sy-@\#$들



