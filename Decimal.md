# Decimal
- `Float`를 사용할 경우 오차가 발생할 수 있다. 부동 소수점을 사용했기 때문에 생기는 문제이다.
- `Decimal`을 사용하면 이러한 문제를 해결할 수 있다. 기본적인 정수에 대해서도 사용 가능하다.
```python
import decimal

x = decimal.Decimal(15)
print(x)
# 15
```

- 소수에 대해서는 인자를 `string`으로 넣어줘야 한다.
```python
x = decimal.Decimal(0.1)
print(x)
# 0.1000000000000000055511151231257827021181583404541015625

x = decimal.Decimal("0.1")
print(x)
# 0.1
print(f"{x:.30f}")
# 0.100000000000000000000000000000
```