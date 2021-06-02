---
title: "Python 딕셔너리 문법 정리"
category: Python
date: 2021-06-02 21:07:05
comments: true
order: 4
---



#### 딕셔너리   

immutable한 키와 mutable한 값이 매핑되어 있는 순서 없는 집합  
값은 중복 될 수 있으나, 키가 중복되면 마지막 값으로 덮어씀   

```python
# 순서가 없기 때문에 인덱스로 접근 못함 , 오로지 키로만 함
d = {'abc' : 1, 'def' : 2}
# d[0] # key erro , 
d['abc'] # 1
```

#### 딕셔너리 선언
   e = {}
   f = dict()

```python
newdict = dict(alice = 5, bob = 20, tony = 15, suzy = 30)
newdict # {'alice': 5, 'bob': 20, 'tony': 15, 'suzy': 30}
```

#### 딕셔너리 변환  
   리스트 속에 리스트나 튜플, 튜플 속에 리스트나 튜플의 값을 키와 value를 나란히 입력하 면, 아래와 같이 dict로 변형할 수 있다.


```python
# 4가지 다 딕으로 변환
name_and_ages = [['alice', 5], ['Bob', 13]]
name_and_ages = [('alice', 5), ('Bob', 13)]
name_and_ages = (('alice', 5), ('Bob', 13))
name_and_ages = (['alice', 5], ['Bob', 13])
dict(name_and_ages) # {'alice': 5, 'Bob': 13}
```

#### 딕셔너리 복사  
   얕은 복사 : 원본과 같은 주소를 참조, 복사된 객체 값이 변경되면 원본도 바뀜  
   깊은 복사 : 참조를 공유 하지 앟음  

```python
a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
b =a.copy()
b['alice'].append(5)
print(b) # {'alice': [1, 2, 3, 5], 'bob': 20, 'tony': 15, 'suzy': 30}
print(a) # {'alice': [1, 2, 3, 5], 'bob': 20, 'tony': 15, 'suzy': 30}
```

```python
import copy
a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
b = copy.deepcopy(a)
b['alice'].append(5)
b # {'alice': [1, 2, 3, 5], 'bob': 20, 'tony': 15, 'suzy': 30}
a # {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
```

#### 딕셔너리 반복문  
   키 값으로 확인  , 순서 보장 못함

```python
a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
for key in a:
    print(key)
    
# alice
# bob
# tony
# suzy
```

```python
a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
for val in a.values():
    print(val)
    
# [1, 2, 3]
# 20
# 15
# 30    
```


```python
a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
for key, val in a.items():
    print("key = {key}, value={value}".format(key=key,value=val))
    
# key = alice, value=[1, 2, 3]
# key = bob, value=20
# key = tony, value=15
# key = suzy, value=30
```


#### 딕셔너리 in  
   키에 의해서 동작

```python
a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
'alice' in a
# True

del a['alice']
a # {'bob': 20, 'tony': 15, 'suzy': 30}
```

#### 참고했습니다.

[https://wikidocs.net/16043](https://wikidocs.net/16043)  