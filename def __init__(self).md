# def __ init__(self):

## __init__
- `기본값 설정하기(initialize)`을 표현한다. 또는 `초기화`라고도 한다.

# Calc(사칙연산) class(클래스) 만들기
```python
class Calc:
    def __init__(self, a, b):
        self.x = a
        self.y = b
    
    def plus(self):
        return self.x + self.y
    
    def minus(self):
        return self.x - self.y
    
    def multiply(self):
        return self.x * self.y
    
    def divide(self):
        return self.x / self.y
```

## self
- self는 `객체의 인스턴스 그 자체`를 말한다. 즉, `객체 자기 자신을 참조하는 매개변수`인 셈이다.
- 파이썬은 클래스의 메소드를 정의할 때 self를 명시한다. 메소드를 불러올 때 self는 자동으로 전달된다. self를 사용함으로 클래스내에 정의한 멤버에 접근할 수 있게된다.

- 우선 self는 `self.x = a`에 정지점을 설정하고 디버깅을 하고 디버깅 창에 'self'라고 치면 아래의 문구가 뜬다.
```python
>>> self
<__main__.Calc object at 0x7fd9c865d370>
```
- `__main__`은 내가 작성 중인 python 파일을 말한다.
- `__main__.Calc`는 작성 중인 python 코드 상의 Calc 클래스를 말한다.
- 즉 self는 Calc 클래스 그 자체 즉 클래스 내에 정의된 `self`는 `클래스 인스턴스`임을 알 수 있다.
- 그래서 self를 다른 단어로 바꿔써도 아무런 문제가 없다. 그저 self라고 쓰는 편이 의미상 편하기 때문에 그렇게 쓰는 것이다.
```python
>>> 어떻게 쓰든 __init__에서 첫 번째로 들어가는 변수명은 Calc 클래스 스스로를 지칭하게 된다.
class Calc:
    def __init__(Calc, a, b):
        Calc.x = a
        Calc.y = b

    def plus(Calc):
        return Calc.x + Calc.y

    def minus(Calc):
        return Calc.x - Calc.y

    def multiply(Calc):
        return Calc.x * Calc.y

    def divide(Calc):
        return Calc.x / Calc.y
```
## __init__ 이해하기
```python
class Calc:
    def __init__(self, a, b):
        self.x = a
        self.y = b
```
- self는 `Calc 클래스 스스로`이다. 따라서 __init__함수는 외부 변수로 a와 b라는 값을 받는다.
- self.x = a -> self가 클래스 스스로이니 self.x는 Calc클래스 내에서 x가 같는 값이다. 즉 self.x = a는 입력받는 외부 변수 a를 Calc 클래스 내의 x의 값으로 정하는 명령어이다.(보통 self.a = a로 사용)

## Calc 클래스를 사용하여 객체(object)인 인스턴스(instance) 생성하기
- Calc 클래스는 위에서 정의하듯 본인 스스로에 추가하여, a, b 두 변수를 받도록 되어 있다. 이제 Calc 클래스에 숫자 두 개를 입력 한다.
```python
i = Calc(2,3)
```
- Calc(2,3)은 Calc 클래스에 숫자 2와 3을 입력하라는 코드이다. 즉 Calc(2,3)은 Calc클래스에 숫자 2와 3이 입력된 상태인 무언가이다. 그리고 그 무언가를 객체(object)라고 부른다.
```python
>>> 파이썬 명령창에 Calc(2,3)을 실행시키면
>>> Calc(2,3)
<__main__.Calc object at 0x7fd9c86950d0>
```
- 그러므로 i = Calc(2,3)은 Calc 클래스에 2와3 상태인 이 객체를 i라고 지정하겠다는 명령어 이다. i도 물론 객체(object)
- 그리고 이 객체 x는 Calc 클래스에 의해 만들어진 객체이다. 이 경우 우리는 객체 x를 Calc의 인스턴스(instance)라고 한다.

## Calc 클래스에 의해 생성된 객체(objcet)인 'i' 인스턴스(instance) 활용하기

- i 라는 Calc 클래스에 2와 3이 입력된 상태인 객체이자 Calc 클래스의 인스턴스(instance)를 만들었다.
- Calc(2,3)을 예시로 든 코드 self.x = 2, self.y = 3이 된다.
-  i 자체가 Calc 클래스에 2와 3이 입력된 상태인 객체(object)이기 때문에 Calc가 가진 함수들을 실행만 시킴으로써 사칙연산을 할 수 있다.
```python
>>> i.plus()
5
>>> i.minus()
-1
>>> i.multiply()
6
>>> i.divide()
0.6666666666
```
- 이 때 plus, minus, multiply, divide 등 `Calc를 이루는 함수(function)`들을 `메소드(method)`라고 한다. 즉, `클래스를 생성하는 이유`는 메소드(method)를 활용하기 위함이다.

## :bulb: 다시 __init__과 self로 돌아와

```python
class Calc:
    def __init__(self, a, b):
        self.x = a
        self.y = b

    def plus(self):
        return self.x + self.y

    def minus(self):
        return self.x - self.y

    def multiply(self):
        return self.x * self.y

    def divide(self):
        return self.x / self.y
```
- __init__은 파이썬 내에서의 약속. 그리고 __init__은 첫 번째 변수로는 보통 self로 표시되는 해당 클래스 스스로를 받도록 되어있다.

## :question: self는 왜 필요한 것인가..

- __init__이 받는 실질적인 주요 변수인 a, b를 클래스(class) 전체가 사용할 수 있도록 만들기 위해서이다.
- __init__함수가 self(예시에서의 Calc)를 받지 않는 다면 __init__ 함수 안에서 Calc 클래스를 불러올 방법이 없어진다.
- 그래서 파이썬에서는 __init__ `첫째 변수가 클래스 스스로를 받도록` 함으로써 self.x = a와 같은 명령어를 사용한다.
- 그래서 만약 __init__(self, a, b)라고 쓰지 않고 __init__(a, b)라고만 쓰게 만들었다면 `받은 변수 a,b`를 `Calc 클래스 전체에서 쓸 수 있도록 저장을 하는 작업`이 `불가능`해진다.
- 즉, __init__(a,b)라고만 해버리면 그냥 __init__함수 안에서만 a, b를 쓸 수 있지 plus, minus 등과 같은 다른 메소드(method) 함수들과는 변수 공유가 불가능해진다.
- __init__과 self를 사용해 효율적인 처리가 가능하다.


## 다른 예시
### Class 다시 보기
- 클래스의 사용 목적 : 변수와 함수를 묶어서 하나의 새로운 객체(타입)으로 만드는 것
- '클래스를 정의한다'의 의미 : 새로운 데이터 타입을 정의한 것. 이를 실제로 사용하려면 인스턴스를 생성해야함
- 인스턴스 : 붕어빵 틀(클래스)에 반죽을 넣어서 만들어진 붕어빵
  - 정의된 클래스를 이용해서 인스턴스 생성하기 : 클래스 이름 뒤에 ()를 넣으면 된다
  ```python
  >>> card1 = Businesscard()
  >>> card1
  <__main__.Businesscard object at 0x0302ABB0>
  ```
  - Businesscard라는 클래스의 인스턴스가 메모리의 한 위치에 생성되고, card1이라는 변수가 이를 구체적인 값, 성격을 확정한다.

```python
>>>  클래스에 메서드 추가하기
class BusinessCard:
  def set_info(self, name, email, addr):
          self.name = name
          self.email = email
          self.addr = addr
```
- 클래스 내부 함수인 메서드를 정의하는 것은 `def` 키워드 사용

```python
>>> 클래서 정의
class Foo:
  def func1():
    print('function 1')
  def fun2(self):
    print('function 2')

>>> 해당 클래스의 인스턴스를 생성
f = foo()

>>> 생성된 인스턴스를 통해 인스턴스 메서드를 호출한다.
f.func2()
# function2
```
- Foo 클래스의 func2 메서드는 메서드의 인자가 self뿐이므로 실제 메서드를 호출할 때 인자를 전달할 필요가 없다.
- func2 메서드의 첫 번째 인자는 self이지만 호출할 때 아무것도 전달 되지 않는 이유는 `첫 번째 인자인 self에 대한 값은 파이썬이 자동으로 넘겨준다.`
- 그렇다면 func1 메서드처럼 메서드를 정의할 때부터 아무 인자도 없는 경우에는 어떻게될까?
  ```python
  >>> f.func1()
  Traceback (most recent call last):
    File "<pyshell#25>", line 1, in <module>
      f.func1()
  TypeError: func1() takes 0 positional arguments but 1 was given
  ```
  - 다음과 같이 인스턴스를 통해 func1() 을 호출하면 오류가 발생한다. 오류메시지는 "func1()은 인자가 없지만 하나를 받았다." 라는 의미이다. 이는 앞서 설명한 것처럼 파이썬 메서드의 첫번째 인자로 항상 인스턴스가 전달되기 때문이다.

```python
>>> 
class Foo:
  def func1():
        print("function 1")

  def func2(self):
        print(id(self))
        print("function 2")
```
- 파이썬 클래스는 그 자체가 하나의 네임스페이스이기 때문에 `인스턴스 생성과 상관없이 클래스 내의 메서드를 직접 호출`할 수 있다.
- 위처럼 지정하고 인스턴스(`f = Foo()`)를 생성 후 주로 사용하는`인스턴스.메서드()` or `클래스.메서드(인스턴스)`



⭐ 네임 스페이스(namespace, 이름공간) - 특정한 객체(Object)를 이름(Name)에 따라구분할 수 있는 범위를 의미한다.

⭐ 클래스(class) - 같은 종류(또는 문제 해결을 위한)의 집단에 속하는 속성(attribute)과 행위(behavior)를 정의한 것.

⭐ 객체(object)
  - 실제로 존재하는 모든 것
  - 함수와 변수(데이터)를 함께 묶는 방법의 하나
  - 속성(attribute) : `객체의 특징 또는 객체에 관해 알고 있는 사항`, 숫자, 문자열 등과 같은 정보로 구성 즉 `속성`은 `객체 안에 포함된 변수(데이터)`이다.
  - 메서드(method) : 파이썬에서 행동 또는 객체에 대해, 객체를 통해 할 수 있는 것. `어떤 일을 하기 위해 호출(call)할 수 있는 코드 덩어리`. 즉 메서드는 객체 안에 포함된 함수이다.
  - `객체 = 속성(변수) + 메서드(함수)` : 즉 객체는 어떤 것에 대한 속성과 메서드를 함께 모으는 한 가지 방법이다. 여기서 `속성 = 정보`, `메서드 = 행동`

## 객체 만드는 순서
  1. class로 설계하기 : 객체가 어떤 모습이고, 어떻게 행동하는 지(객체의 속성과 메서드) 정의한다. 객체의 설명이나 설계도를 `클래스(class)`라고 한다. 즉 우선 객체를 생성하기 위한 틀인 class를 만든다.
  2. instance 만들기 : 설계도 클래스를 이용해 실제 객체를 만드는 것이다. 이때 객체를 해당 클래스의 `인스턴스(instance)`라고 한다.

## step 1. class를 만들어 설계하기
- 클래스 구성요소 : 클래스 이름, 클래스 메서드(함수)
  1. class에 클래스 이름 지정. 보통 대문자로 시작한다. `[class 클래스 이름]`
  2. def로 메서드 작성. 메서드의 첫 번째 매개변수는 보통 self를 지정 `[def 메서드(self)]`
  ```python
  >>> 간단한 Dog 클래스 만들기
  class Dog:
    def bark(self): # 메서드
      print('멍')   # 메서드
      # 클래스 이름 : Dog, 클래스 메서드 : bark
  ```
## step 2: instance 만들기
- 클래스를 만들었다면 클래스를 이용해 실제 객체를 만든다. 이 때 객체를 해당 클래스의 인스턴스
- Dog의 인스턴스를 만드려면 다음과 같은 코드가 필요하다. `[인스턴스 = 클래스()]`
  ```python
  class Dog:
    def bark(self):
      print('멍!')
  # 인스턴스 만들기
  myDog = Dog()
  ```
  - 클래스 Dog에 myDog(객체)라는 이름을 할당하였는데 이 myDog이 Dog의 인스턴스가 된다.

## step 3 :  객체의 속성과 메서드 사용하기
- 아직까지 Dog에 아무런 속성이 없으므로 `[인스턴스.속성]`으로 몇 가지 속성을 추가할 수 있다.
```python
class Dog:
  def bark(self):
    print('멍!')

myDog = Dog()

>>>  속성 추가하기
myDog.name = '백구'
myDog.color = 'white'
myDog.size = 'big'

>>> 객체의 속성 출력
print('My dog is', myDog.name) # My dog is 백구
print('He is', myDog.color) # He is white
print('He is', myDog.size) # He is big

>>> 메서드 사용하기
myDog.bark() # 멍! 이 출력됨
```
- Dog의 `클래스(class)`를 만들고 이 클래스에 myDog라는 `객체`의 이름을 할당한 뒤`(인스턴스)`, myDog의 특징`(속성)`과 짖는 행동`(메서드)`를 출력했다.