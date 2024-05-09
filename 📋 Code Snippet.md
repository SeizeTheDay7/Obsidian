**키에 대한 예외 처리**
```python
def get_first_valid(info, keys, default=''):
for key in keys:
	if key in info:
		return info[key]
return default

# 딕셔너리의 각 키에 대해 유효한 값을 찾기
illustrator_keys = ['Illustrator', 'Makeup charge', '3D Modeler', 'illustrator', 'Illustrator Live2D Designer']
debut_keys = ['Debut Stream', 'Debut', 'Debut date']
height_keys = ['Height', 'Heigh', 'height']

# 각 필드에 대한 값 설정
illustrator = get_first_valid(info, illustrator_keys, '')
debut = get_first_valid(info, debut_keys, '')
height = get_first_valid(info, height_keys, '')
unit = info.get('Unit', '')
```

**문자열 날짜 변환**
```python
date = "August 12, 2020"

try:
    debut_date = datetime.strptime(debut, "%B %d, %Y").strftime("%Y.%m.%d")
except ValueError:
    debut_date = '미상'

print(debut_date) # 2020.08.12
```

