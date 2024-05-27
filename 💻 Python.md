

### 리스트 컴프리헨션

```python
new_list = [expression for item in iterable]
```

```python
numbers = [1, 2, 3, 4, 5]
squares = [number ** 2 for number in numbers]
print(squares)  # [1, 4, 9, 16, 25]
```

- **expression**: 새 리스트에 넣을 표현식
- **item**: 현재 반복 중인 개체의 개별 항목
- **iterable**: 반복 가능한 객체(예: 리스트, 튜플, 문자열 등)