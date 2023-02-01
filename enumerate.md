# enumerate 함수

- 반복문을 사용할 때 리스트의 순서 값, 즉 인덱스의 정보가 필요한 경우에 사용
- `리스트의 원소에 순서값을 부여해주는 함수`이다.
```python
item = ['First', 'Second', 'Third']
data = enumerate(item)
print(data, type(data))

<Class 'enmerate'> # enumerate 함수는 입력으로 받은 데이터와 인덱스 값을 포함하는 enumerate 객체를 리턴해준다.
```
```python
item = ['First', 'Second', 'Third']
for i in enmerate(item):
  print(i)
# (0, 'First')
# (1, 'Second')
# (2, 'Third')
```
- enumerate 함수를 사용하여 for문을 돌려보면 리스트의 원소와 인덱스가 튜플 형태로 담겨있다.
```python
item = ['First', 'Second', 'Third']
for i, val in enmerate(item):
  print("{} 번쨰 값은 {}입니다".format(i, val)) 

0 번쨰 값은 First입니다 
1 번쨰 값은 Second입니다 
2 번쨰 값은 Third입니다
```