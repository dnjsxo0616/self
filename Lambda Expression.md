# 람다(lamdba)
```python
lambda 매개변수 : 표현식 == lambda 인자 : 표현식
```
- 람다 표현식은 메서드로 전달할 수 있는 익명 함수를 단순화한 것이라고 할 수 있다.

:bulb: 예시
```python
def hap(x, y):
  return x + y

  hap(10, 20) # 30
```
```python
>>> lambda 형식
(lambda x,y : x + y)(10,20) # 30
```

## lambda 함수와 map

### map 함수의 모양과 사용법

- map(함수, 리스트나 튜플)

```python
# 1. 일반 함수 버전
def plus_two(x):
  return x + 2

result1 = list(map(plus_two, [1, 2, 3, 4, 5]))
or
result1 = list(map(plus_two, range(1, 6)))
print(result1) # [3, 4, 5, 6, 7]

# 2. 람다 함수 버전

result2 = list(map((lambda x : x+2), [1, 2, 3, 4, 5]))
print(result2) # [3, 4, 5, 6, 7]
```

## lambda와 sorted 함수

- `sorted`함수의 경우 `key`위치인자에 함수를 보내서, 함수에서 저장한 결과값에 따라서 정렬을 할 수 있다.

```python
# 1. 일반 함수 버전
def my_key(string):
  return len(string.strip())

target = ['cat', 'tiger', 'dog', 'snake']
print(sorted(target, key = my_key))

# 2. 람다 함수 버전

target = ['cat', 'tiger', 'dog', 'snake']
print(sorted(target, key = lambda x : len(x.strip())))
```
:star: 주의사항
1. sort() 함수는 sorted() 함수와 다르게 Return Value가 존재하지 않음

2. Key 함수를 사용하면 List 내부의 Element에서 특정 조건에 따라 정렬할 수 있음

3. key는 정렬 시 비교할 값을 Return하는 함수이며, x는 리스트 내 Element를 의미한다.

## lambda와 reduce 함수
```python
>>> reduce(함수, 시퀀스(문자열, 리스트, 튜플))

from functools import reduce
reduce(lambda x, y : x + y, [0, 1, 2, 3, 4]) #10
```

## lambda와 filter 함수
```python
>>> filter(함수, 리스트)
# 리스트에 들어있는 원소들을 함수에 적용시켜서 결과가 참인 값들로 새로운 리스트로 만들어준다.

# 1. 일반 함수 버전

def is_even(x):
  return x % 2 == 0

result1 = list(filter(is_even, range(10))) # [0~9]
print(result1) # [0, 2, 4, 6, 8]

# 2. 람다 함수 버전

result2 = list(filter((lambda x : x % 2 == 0), range(10))) # [0~9]
print(result2) # [0, 2, 4, 6, 8]
```