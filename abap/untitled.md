# Input Checks

## Foreign key

Foreign key는 관계형 데이타베이스에서 테이블 간의 연결을 정의하며, data integrity\(무결성\), data consistency\(일관성\)를 보장하기 위해 사용된다. Foreign key는 abap dic에만 정의 돼 있으며 실제 DB에는 존재하지않는다.

### Foreign key Table and Check Table

다른 tab의 primary key를 참조하는 table이 Foreign key tab 참조 되는 table이 check tab이라고 한다. 즉 foreign key tab은 check tab의 primary key를 자신의 Foreign key field로 사용한다. check table은 referenced table이라고도 함. Foreign key로 연결된 field는 두 tab 간에 field name\(data element의 name\)이 달라도 같은 data type과 length를 가져야 한다. 또 같은 domain을 사용해야한다.

### Check field

Foreign key가 check field와 연결돼 있다는 것은 Foreign key field에 입력되는 값은 Check table에 값이 있는지 확인 과정을 거치게 된다는 것을 의미한다. Check table에 값이 없으면 Foreign key field에 값이 입려되지 않는다.  check field가 check table의 value를 check해준다. 

#### Generic key 

check tab에 여러 개의 key field가 있으 때 그 중 체크할 필요가 없는 field에 Generic  key를 설정하면 Check tab에서 그 필드의 값을 무시하고 체크하게 된다.

### Domain의 제한 사항들

#### Value Table

해당 domain을 사용하는 모든 data element를 사용하는 tab들은 value tab으로 지정된 tab 값만 쓸 수 있음. 

#### Fixed value

domain의 특정값을 제한하는 것,  Value Range라는 탭에서 domain의 fixed values을 지정.





