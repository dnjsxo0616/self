# 문자열 나누기 Split(), 결합 join()
- 알고리즘 문제를 풀다 보면 문자열(공백)나누기와 결합을 요구하는 문제
- 문자열을 리스트로 나누거나, 리스트를 문자열로 결합할 때

## split()
: 기준 문자를 기점으로 분리 후 리스트로 반환  
`:split("나눌 기준 문자")`

### 1. 문자 기준
: 0을 기준으로 나누고 싶을 때
```python
str = "Welcome Python World"

str.split("o")
#['Welc', 'me Pyth', 'n W', 'rld']
```

### 2. 공백 기준
: 공백을 기준으로 나누고 싶을 떄
```python
str = "Welcome Python World"

str.split()
# ['Welcome', 'Python', 'World']
```

## join()
: 문자열을 합친다는 개념

- 위에서 나누었던 결과를 바탕으로 합치면
### 1.문자
```python
str = ['Welcome', 'Python', 'World']

".".join(str)
# 'Welcome.Python.World'
```

### 2. 공백
```python
str = ['Welcome', 'Python', 'World']

" ".join(str)
# 'Welcome Python World'
```

:bulb: join()함수 : 튜플, 딕셔너리에서도 가능하다.
- 튜플
```python
str_tuple = ("Welcome", "Python", "World")

"_".join(str_tuple)
# 'Welcome_Python_World'
```

- 딕셔너리
```python
str_dict = ('key1':'Welcome', 'key2':'Python', 'key3':'World')

"_".join(str_dict)
# 'key1_key2_key3'
```
- key값 1
```python
str_dict = ('key1':'Welcome', 'key2':'Python', 'key3':'World')

"_".join(str_dict.key())
# 'key1_key2_key3'
```

- value값
```python
str_dict = ('key1':'Welcome', 'key2':'Python', 'key3':'World')

"_".join(str_dict.values())
# 'Welcome_Python_World'
```
---

# :star: 정리

* 문자열 -> 리스트  

- ### HOW?
> plit() : 기준 문자로 나구기

* 리스트, 튜플, 딕셔너리 -> 문자열
---
- ### HOW?
> join() : 합치기

- ### 튜플이란?  

: 자료 구조로, 배열처럼 여러 개의 데이터를 열거하여 담아두는 데에 사용한다.
> 리스트와 동일하게 여러 객체를 모아서 담는다.   숫자, 문자, 객체, 배열, 튜플 안의 튜플 전부 가능하다. 하지만 튜플 내의 값은 `수정이 불가`하다. 추가도, 삭제도 안 된다. 한번 만들어지면 끝까지 가지고 가야 된다. ( )로 사용하고, ( )가 없어도 동일하게 사용 가능하다.

 - ### 배열과의 차이는??
> 배열은 여러 개의 데이터들을 모은 집합. `추가와 삭제가 가능`하다. [ ]로 사용한다.
---
### 딕셔너리란(Dictionary / dict)

> key와 value를 한 쌍으로(1대 1로) 저장하는 자료형이다.  딕셔너리를 생성하기 위해서는 중괄호 사이에 key : value 형태로 정의하고 쉼표로 구분한다. 즉, 아래와 같은 방식으로 딕셔너리를 정의할 수 있다.

### Key / value

> 딕셔너리의 key 값은 정수형을 포함한 어떠한 자료형도 가능합니다. <dv/> 특정 key 값에 해당하는 value 값에 접근하려면, 딕셔너리명[key값]의 형태로 사용합니다. 단, 하나의 딕셔너리에 같은 key 값이 동시에 저장될 수는 없습니다.
