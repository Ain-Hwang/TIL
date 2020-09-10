---
description: Java를 이용한 알고리즘 훈련
---

# Algorithm

## 1. 입출력과 사칙연산

1. Hello World 출력하기

Java

```text
public class Main{
    public static void main(String[] args) {
        System.out.printf("Hello World!");
    }
}
```

**2. 사칙연산 \(파이썬\)**

```text
a,b=input().split()

a=int(a)
b=int(b)

print(a+b)
print(a-b)
print(a*b)
print(a//b)
print(a%b)
=====================================================

a,b=map(int, input().split())

print(a+b)
print(a-b)
print(a*b)
print(a//b)
print(a%b)
```

* split\(\) : 문자를 구분짓는 기준 \(\) 안에 값 없이 그냥 쓰면 공백을 기준으로 input값을 각각 a와 b로 구분 지음 
* map\(\): 여러 개의 데이터를 한 번에 다른 형태로 변환, 여러 개의 데이터를 담고 있는 list나 tuple을 대상으로 주로 사용하는 함수

