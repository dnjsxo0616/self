# lambda

```python
dict_list = {
    'apple':2,
    'banana':3,
    'chicken':1,
    }

dict_ans = sorted(dict_list, key = lambda x : x[0])
print(dict_ans)
# ['apple', 'banana', 'chicken']
```

```python
dict_list = {
    'apple':2,
    'banana':3,
    'chicken':1,
    }

dict_ans = sorted(dict_list, key = lambda x : x[1])
print(dict_ans)
# ['banana', 'chicken', 'apple']
```


```python
dict_list = {
    'apple':2,
    'banana':3,
    'chicken':1,
    }

dict_ans = sorted(dict_list.items(), key = lambda x : x[0])
print(dict_ans)
# [('apple', 2), ('banana', 3), ('chicken', 1)]
```

```python
dict_list = {
    'apple':2,
    'banana':3,
    'chicken':1,
    }

dict_ans = sorted(dict_list.items(), key = lambda x : x[1])
print(dict_ans)
# [('chicken', 1), ('apple', 2), ('banana', 3)]
```

# chr() ord()

- chr()는 정수값 -> 문자, ord()는 문자->정수값
```python
n = ord(input()) #a
print(chr(n+1)) #b
```
```python
c = int(input()) # 65
print(chr(c)) # A
#c 에 저장되어 있는 정수 값을 유니코드 문자(chracter)로 바꿔 출력한다. 
```

# fomat함수

- 포메팅이란?
    - 문자열 중간 중간에 특정 변수의 값을 넣어주기 위해 사용

## format 함수 사용법

- 중괄호 {, }안에 포매팅을 지정하고 format 함수의 인자로 값들을 넣는다.
```python
a = 2
b = 3

s = '구구단 {0} x {1} = {2}'.fomat(a, b, a*b)
print(s)
```
## -자리수와 소수점 표현하기

```python
>>> 정수 N자리
s15 = '정수 3자리 : {0.03d}, {1:03d}'.fomat(12345, 12)
print(s15)

>>> 소수점 N자리
s16 = '아래 2자리 : {0:0.2f}, 아래 5자리 : {1:0.5f}'.format(123.1234567, 3.14) # 123.12 , 3.14000


a=input()
a=float(a) # 3.141592
print( format(a, ".2f") ) # 3.14
# 소수점 이하 두 번째자리까지 반올림

>>> f-sting 이용
a, b = map(int, input().split()) # 10 3

print(f'{a/b:.2f}') # 3.33


a, b, c = list(map(int, input().split())) # 1 2 3
print(f'{a+b+c} {((a+b+c)/3):.2f}')
# 6 2.00
```

## 비트시프트 연산

### 2의 거듭제곱 배로 곱해 출력하기

```python
a = int(input())
print(a<<1) # a에 2^1이 곱해진다

a, b = map(int, input().split()) # 1 3
print(a<<b) # a에 2^b가 곱해진다  1*8
```

## if - else 조건문 한 줄로 표현하기
```python
a, b = map(int, input().split()) # 1 3 ## 4 3
c = (a if (a>=b) else b)
d = ('home' if (a>b) else 'hi')
print(int(c)) # 3 ## 4
print(d) # hi ## home

>>> 가장 작은 값 출력(두 개 조건)
a, b, c = map(int, input().split())
d = ((a if (a<b) else b) if ((a if a<b else b)<c) else c) # 3 -1 5
# 앞에서 a와b를 비교 그 후 c랑 비교하여 크면 앞에 식의 값 c가 더 작으면 c출력
print(d) # -1
```

## if - elif
```python
>>> if문으로만 하면 다 돌아감
a, b, c = map(int, input().split()) # 1 2 4
if a % 2 == 0:
    print(a)
if b % 2 == 0:
    print(b)
if c % 2 == 0:
    print(c)
""""
2
4
""""

>>>if - elif에서 돌다가 조건이 맞으면 출력하고 끝
a, b, c = map(int, input().split()) # 1 2 4 ## 2 4 8
if a % 2 == 0:
    print(a)
elif b % 2 == 0:
    print(b)
elif c % 2 == 0:
    print(c)
"""
2
"""
```