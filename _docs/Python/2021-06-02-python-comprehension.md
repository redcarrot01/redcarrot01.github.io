---
title: "Python Comprehension"
category: Python
date: 2021-06-02 11:07:05
comments: true
order: 2
---



리스트 , 집합(set), 딕셔너리(dictionary) 자료형에 대해 사용

#### 리스트 : 반복문을 사용한 Comprehension

~~~python
>>> [x for x in range(10)]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
~~~

#### 리스트 : 조건문 사용한 Comprehension

~~~python
>>> [i for i in range(30) if i%2 == 0]
[0, 2, 4, 6, ... 28]
~~~

#### 리스트 : 두 개의 반복문 사용

~~~python 
>>> ['a', 'b', 'c']
>>> b = ['1', '2', '3']
>>> [i + j for i in a for j in b]
['a1' , 'a2','a3', 'b1', ... 'e3']
~~~
중첩 for문 이라고 볼 수 있다. 아래와 같다.

~~~python
>>> new_list = []
>>> for i in a:
>>> 	for j in b:
>>>     	new_list.append(i+j)    
~~~

#### 리스트 : 두 개의 조건문 사용

~~~python
>>> [i for i in range(50) if i %2 ==0 if i%3 ==0]
[0, 6, 12, ... 48]
~~~

#### 리스트 : 조건문에서 else 사용

~~~python
>>> ['even' if i%2 ==0 else 'odd' for i in range(10)]
['even', 'odd', 'even', ...]
~~~

#### 리스트 : 조건문에서 elif 사용
else if 조합으로 사용
~~~python
>>> ['zero' if i==0 else 'even' if i%2 ==0 else 'odd' for i in range(10)] 
['zero', 'odd', 'even', 'odd', 'even', ...]
~~~

#### 튜플에서 사용

~~~python
>>> [(x, y) for x in ['쌈밥', '치킨', '피자'] for y in ['사과', '아이스크림', '커피'] ]
[('쌈밥', '사과'),
 ('쌈밥', '아이스크림'),
 ('쌈밥', '커피'),
 ('치킨', '사과'),
 ('치킨', '아이스크림'),
 ('치킨', '커피'),
 ('피자', '사과'),
 ('피자', '아이스크림'),
 ('피자', '커피')]
~~~

#### 딕셔너리 : [] -> {} 이용하면 set 

~~~python
>>> [ x+y for x in range(10) for y in range(10) ]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18]
>>> { x+y for x in range(10) for y in range(10) }
{0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18}
~~~

#### 딕셔너리 : 중괄호 + key-value

**⚠ 연습 필요**

~~~python
>>> st = ['철수', '영희', '길동', '순희']
>>> { s : 0 for s in st}
{'철수': 0, '영희': 0, '길동': 0, '순희': 0}
~~~

~~~python
>>> scores = {'철수': 50, '영희': 80, '길동': 90, '순희': 60, '전학생': 100}
>>> scores = {name: score for name, score in scores.items() if name != '전학생'}
>>> print(scores)
{'길동': 90, '순희': 60, '영희': 80, '철수': 50}
~~~

~~~python
>>> grades = {name : 'PASS' if value > 70 else 'NO' }
>>> print(grades)
{'길동': 'PASS', '순희': 'No-PASS', '영희': 'PASS', '철수': 'No-PASS'}
~~~