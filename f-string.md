# 파이썬의 f- string 사용법

## 1/2 파이썬 실습 3번 문제
```python
# 이름과 태어난 년도를 입력 받고, 출력하세요.(단, 태어난 년도를 나이로 변환해서 출력하세요.)
name = input('이름을 입력해주세요 > ')
year = int(input('태어난 년도를 입력해주세요 > '))
print(f'저의 이름은 {name}이고, 올해 나이는 {2023 - year + 1}세 입니다.')
```
---

## String formatting - 문자열 포매팅
: 문자열을 내가 원하는 형식에 맞추어 표현하는 방법

```python
>>> int_val = 12345678
>>> float_val = 1234.5678
>>> str_val = "Hello"
>>> print(f"{int_val} {float_val} {str_val}")
12345678 1234.5678 Hello
>>> print(f"{12345678} {1234.5678} {'Hello'}")
12345678 1234.5678 Hello
```

```python
# 문자열 맨 앞에 f를 붙이고, 출력할 변수, 값을 중괄호 안에 넣습니다.
s = 'coffee'
n = 5
result1 = f'저는 {s}를 좋아합니다. 하루 {n}잔 마셔요.'
print(result1)
```

즉, 앞에 소문자 f를 쓰고 뒤에 큰 따옴표 혹은 작은 따옴표로 문자열을 작성하면 된다.