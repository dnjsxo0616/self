# Dictionary

- key 값은 `중복이 되지 않는다`. 중복으로 추가하는 경우 마지막으로 추가한 key : value 쌍이 남게 된다.
- `key`에는 `immutable(변경불가)` 자료형만 올 수 있다.

# keys - 딕셔너리의 key(키) 뽑기

- 딕셔너리 `.keys()` 함수를 통해서 딕셔너리의 키(key)들을 한 번에 볼 수 있다.

```python
dic = {
    '이름': '홍길동',
    '번호':'010-1234-5678',
    '거주지':'서울'
    }

for key in dic.keys():
    print(key)
"""
이름
번호
거주지
"""
```

# values - 딕셔너리의 value(값) 뽑기

- 딕셔너리.vaules() 함수를 통해서 딕셔너리의 값(vaule)들을 한 번에 볼 수 있다.

```python
dic = {
    '이름': '홍길동',
    '번호':'010-1234-5678',
    '거주지':'서울'
    }

for value in dic.values():
    print(value)
"""
홍길동
010-1234-5678
서울
"""
```

# items - 딕셔너리 key, value 전부 뽑기

- 딕셔너리.items() 함수를 통해서 딕셔너리의 key, value을 한 번에 볼 수 있다.

```python
dic = {
    '이름': '홍길동',
    '번호':'010-1234-5678',
    '거주지':'서울'
    }

for key, value in dic.items():
    print(key, value)
"""
이름 홍길동
번호 010-1234-5678
거주지 서울
"""
```

# 딕셔너리 생성

```python
>>> 직접 생성
di1 = {'a': 0, 'b': 1, 'c': 2, 'd': 3}
# {'a': 0, 'b': 1, 'c': 2, 'd': 3}
>>> zip 함수를 사용해 dict 생성: zip(key list, value list)
di2 = dict(zip('abcd',range(4)))
di3 = dict(zip('abcd',[0,1,2,3]))
# {'a': 0, 'b': 1, 'c': 2, 'd': 3}
```
# 최대 value에 대한 key 값 찾기

## 1. 최대 value가 `1개`일 때

```python
dic = {'a':0, 'b':1, 'c':2, 'd':3}

>>> max(이름, key = 이름.get)
tmp = max(dic, key = dic.get)
print(tmp) # d
```
- 만약 최대 value 가 2개 이상인 상황에서 1번의 방법(max 함수)을 사용하면, value의 최댓값 중 맨 앞에 있는 key인 'c' 하나만 출력한다.

## 2. 최대 value가 `2개` 이상일 때

```python
dic = {'a':0, 'b':1, 'c':2, 'd':3}

>>> 리스트 컴프리헨션 이용
tmp = [key for key, value in dic.items() if max(dic.values()) == v]
print(tmp) # ['c', 'd']
```

# value의 최대값

```python
dic = {'a':0, 'b':1, 'c':2, 'd':3}

print(max(dic.values()))
# 3
all_values = dic.values()
print(all_values)
# dict_values([0, 1, 2, 3])
max_vaule = max(all_values)
print(max_vaule)
# 3
```

# del - 딕셔너리에서 key, value 한쌍 지우기

```python
dic = {'a':0, 'b':1, 'c':2, 'd':3}

del dic['a']
print(dic)
# {'b':1, 'c':2, 'd':3}
```

# clear - 딕셔너리 key, value 모두 지우기

```python
dic = {'a':0, 'b':1, 'c':2, 'd':3}

dic.clear()
print(dic)
# {}
```