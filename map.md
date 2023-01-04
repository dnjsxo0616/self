# map()함수

## 파이썬 map()함수란?
: 각 요소들에 특정한 함수를 적용시킬 때 쓰는 함수이다.  
: 첫 번째 인자(input)으로 함수를 받아서   
: 두 번째 인자(input)인 반복 가능한 객체의 모든 요소에 적용!

## map()을 왜 쓸까:question:
: 1개의 입력이 아니라, 여러개가 입력된 경우 각각의 요소들에 대해 특정한 함수를 적용시키고 싶을 때 ['1','2']->[1, 2] 각각의 '1', '2'를 변환  

## map 흐름
1. 문자열을 각각 쪼갠 요소를 가진 리스트 변환
```python
# a = 숫자 2 5를 원한다.
a = input()
print (a) # '2 5'를 원한다.

b = a.split() #['2', '5'] -> 2와 5를 쪼개줌
```
`input().split까지는 리스트다`  

2. 각 요소를 숫자로 변환 -> map()
```python
c = map(int, b)
print(C) # ~map...어쩌구나옴
```
3. 각각 변수에 저장
```python
d, e = list(c) # list(c)가 [2, 5]
print(d, e) # 각각 2, 5
```
- 위 과정을 모두 합치면
```python
d, e = list(map(int, input().split()))
#여기서 list는 생략가능
d, e = map(int, input().split())
# 2 5
```
## 결론 int로 바꾸고 싶으면
 ```python
 numbers = list(map(int, input().split()))
 # 첫 번째꺼 d에 넣고 싶으면
 d = numbers[0]
 # 두 번째꺼 e에 넣고 싶으면
 e = numbers[1]
 ```

## int로 적용 시키고 싶은 경우
- 입력 : 1 2 3 4 5

### 1. case
: 만약 사용자의 입력을 받는데, 입력 받는 수가 많고 각각의 타입을 변환할 때
```python
input() # '1 2 3 4 5'
input().split() #['1', '2', '3', '4', '5']
# 문자형이기 때문에 int형으로 바꿔주려면
map(int, ['1', '2', '3', '4', '5'])
map([1, 2, 3, 4, 5]) # 정수형 1 2 3 4 5로 변환
```
```python
a, b, c, d, e = map(int, input().split())
print(a, b, c, d, e)
# a b c d e
```
```python
# 하나의 묶음으로 담기 위한 리스트로 받고 싶을 떄
a =list(map(int, input().split()))
print(a)
# [1, 2, 3, 4, 5]
```
### 2. case
: 리스트의 합을 구하고 싶다.
```python
a = ['1', '2', '3']
result = 0
for n in a:
  result += int(a)
print(result) #6
```
```python
n = ['1', '2', '3']
new = []
for a in n:
  new.append(int(a))
print(new) # [1, 2, 3]
```
```python
n = ['1', '2', '3']
new_n = map(int, n)
print(list(n))
# [1, 2, 3] 위의 코딩의 값을 한줄로 표시 가능
```

## :question: split() 함수로 문자열 분리가 가능하다. 그럼 input()과 다른 점은?

- 숫자를 1개씩 받는 방법이란 건  
: 1 2를 입력받는다 하면 input(1,2)하면 그 결과는 "1 2"로 묶이게 된다. 이 때 1따로 2 따로 받는 방법을 의미한다. 