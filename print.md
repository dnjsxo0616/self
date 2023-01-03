# 함수 print() 옵션

## 1. sep(separation)

```python
A,B = map(int, input().split()) # 7 3입력
print(A+B, A-B, A*B, A//B, A%B, sep="\n")
"""
10
4
21
2
1
""" #결과마다 줄바뀜으로 출력
```

## 2. end
: end 옵션을 사용하면 그 뒤의 출력값과 이어서 출력한다.(즉, 줄바꿈을 하지 않게 된다.)

```python
print("I like", end=" ")
print("money")
# I like money
```

: end=' ' 사이에 무언가를 입력하게되면, sep와 비슷한 기능을 한다.(구분자를 사용할 수 있다) 첫번째 출력문과, 두번째 출력문 사이에 end에 넣어준 문자열이 출력된다.
```python
print("I like", end=" gold and ")
print("money")
# I like gold and money
```

## 3.format
:포매팅을 통해 특정 서식에 따라 문자를 출력할 수 있다. 부분적으로 문자열을 바꾸어 반복적으로 출력할 때 유용하다.

- 월,일 숫자를 바꾸고 싶을 떄
```python
print("{0}월{1}일 입니다.".format(10,31))

출력 :  10월31일 입니다.
```

- %기호를 사용한 format
```python
print("%s을 %d개 주세요."%("아이스크림", 10))
출력 : 아이스크림을 10개 주세요.
```

## Escape

\n  : 줄바꿈

\t :   탭(TAP)

\\  :  '\' 출력

\'  :  작은따옴표 출력

\"  :  큰따옴표 출력

\b  :  백스페이스

```python
print("줄바 \n 꿈")
print(" \"큰 따옴표 출력\"")
print(" \\ 역슬래쉬 출력")
print("골뱅이는 백스페이스 때문에 지워지겠지 @\b")

-----------------출력-------------------
줄바
 꿈
 "큰 따옴표 출력"
 \ 역슬래쉬 출력
골뱅이는 백스페이스 때문에 지워지겠지 
```
