# 출력 형식

## 1. 변수 포맷(`%d`, `%s`,...)과 `%`를 사용
  - 변수 포맷은 문자열일 경우 `%s`를,
  - 문자의 경우 `%c`를, 정수의 경우 `%d`, 실수의 경우 `%f`
```python
a = 5
print('A is %d' %a)
>> A is 5

b = 'apple'
print('B is %s' %b)
>> B is apple

```

## 2. format 함수를 이용

- format 함수를 이용하면 직접 변수의 type을 명시하지 않더라도, 순서 혹은 이름을 명시하여 원하는 변수를 포맷에 맞춰 넣어줄 수 있다.
- 숫자를 적게되는 경우에는 format 함수에 적게되는 변수에 번호를 0번부터 붙였을 때 몇 번째 값인지를 명시하는 것이다.
- 숫자 대신 새로운 이름을 붙여 적는 것도 가능하다.
```python
a, b = 5, 'apple'

print('A is {0}'.format(a))
>> A is 5

print('A is {new_a}'.format(new_a=a))
>> A is 5

print('B is {0}'.format(b))
>> B is apple

print('B is {}'.format(b))
>> B is apple

print("A is {0} and B is {1}".format(a, b))
>> A is 5 and B is apple

print("A is {} and B is {}".format(a, b))
>> A is 5 and B is apple

print("A is {2} and B is {3}".format(a, b))
>> IndexError: Replacement index 2 out of range for positional args tuple
```

## 3. f 문자열 포맷을 이용

```python
a, b = 5, "apple"

print(f"A is {a}")
>> A is 5

print(f"B is {b}")
>> B is apple

print(f"A is {a} and B is {b}")
>> A is 5 and B is apple
```

## 4. 소수점 맞춰 출력하기
- `%`를 사용한다.
- format 함수를 이용했을 경우 기존 포맷이 `{0}`이었다면 그 뒤에 `:`을 붙여 포맷을 지정한다.
- f포맷을 이용할 경우 {}안에 다 넣어준다.

```python
# 소수점 4자리까지 출력
a = 33.567268
print('%.4f' %a)
>> 33.5673

# format 함수이용
a = 33.567268
print('{0:.4f}'.format(a))
>> 33.5673

# f 포맷
a = 33.567268
print(f'{a:.4f}')
>> 33.5673
```
