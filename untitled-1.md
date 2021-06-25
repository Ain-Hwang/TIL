---
description: Python로 알고리즘
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

## 2. if 

1. 학점 계산하기

```text
print("점수를 입력하세요")
score = int(input())

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
else:
    print("F")
```

2. 년계산하기

```text
year = int(input())

if year % 4 == 0 and year % 100 != 0 or year % 400 == 0:
    print("1")
else:
    print("0")
```

3.  사분면 고르기 

```text
print("x값을 입력하세요")
x = int(input())
print("y값을 입력하세요")
y = int(input())

if x > 1 and y > 1:
    print("1")
elif 0 != x < 1 and y > 1:
    print("2")
elif 0 != x < 1 and 0 != y < 1:
    print("3")
elif x > 1 and 0 != y < 1:
    print("4")
```

## 3. for

1. 입력 받은 횟수 만큼 더하기 

```text
a = int(input())

for i in range(1, 10):
    print(a, "*", i, "=", a*i)
```

2.  입력 받은 횟수 받음 a,b를 입력받아 더하기

```text
z = int(input())

for i in range(z):
    a, b = map(int, input().split())
    print(a+b)
```

3. 입력받은 횟수만큼 누계합하기 

```text
# n = int(input())

# for i in range(n+1):
#     i = i+
# print(i) // 이렇게 해도 결과는  똑 같음


n = int(input())
sum = 0

for i in range(n+1):
    sum = sum+i
print(sum)
```

4. input말고 sys.stdin.readline\(\) 을 사용해 입력 받은 값 출력하기 

```text
import sys
n = int(input())

for i in range(n):
    a, b = map(int, sys.stdin.readline().split())
    print(a+b)
```

5. N찍기

```text
n = int(input())3

for i in range(1, n+1):
    print(i)
```

6. 기찍N

```text
n = int(input())

for i in range(n):
    print(n-i)
```

7. A + B - 7

```text
cases = int(input())

for i in range(cases):
    a, b = map(int, input().split())
    # hab = a+b
    print('Case #%s: %s' % (i+1, a+b))
```

8.  A + B - 8 

```text
cases = int(input())

for i in range(cases):
    a, b = map(int, input().split())
    # hab = a+b
    print('Case #%s: %s + %s = %s' % (i+1, a, b, a+b))
```

9. 별 찍기 1

```text
a = int(input())

for i in range(1, a+1):
    print('*'*i)
```

10. 별찍기 2

```text
a = int(input())

for i in range(1, a+1):
    print(' '*(a-i)+'*'*i)
```

