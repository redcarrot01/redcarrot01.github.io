---
title: "Python 문자열 함수 정리"
category: Python
date: 2021-06-02 21:07:05
comments: true
order: 3
---



#### 대문자, 소문자(upper, lower)  
문자열의 원본이 바뀌지는 않는다.  

```python
string = "Hello"
string.upper() # 대문자로 변환
string.lower() # 소문자로 변환
```

#### 문자열 바꾸기(replace)

```python
string = "hi world ye"
string.replace("i", "a") # 'ha world ye'
string.replace("ye","") # 삭제 : 'hi world '
```
#### 문자열 찾기(find, count)  
위치 리턴, 없을 경우 -1 리턴

```python
string = "hi world ye"
string.find("wo") # 3

string.count('i') # 1
string.find("maroon") # -1
```

#### 슬라이싱
```python
string = "My favorite song is snowman by sia"
string[:-2] #'My favorite song is snowman by s'

# 2개씩 step
# M aoiesn ssomnb i
string[::2]

# Reverse
# ais yb namwons si gnos etirovaf yM
string[::-1] 
```

#### 문자열 분리 및 결합(split, join)  
split : 리턴할 때 결과는 리스트, 생략할 경우 공백 기준 분리  
문자열.join(리스트) : 리스트 원소 사이에 문자열을 삽입, 단, 리스트의 원소 모두 str

```python
string = "app baa cdd sdd"
string.split() # ['app', 'baa', 'cdd', 'sdd']

string = "1a2a3a4a"
# ['1', '2', '3', '4', '']
string.split("a")

li = [1, 2, 3, 4]
# 리스트의 원소는 모두 str 타입이어야 한다. 아닐경우 오류발생
# 오류발생!
" ". join(li)
```

#### 공백 제거(strip)

```python
string = "       Hello World!       "

string.strip()
string.lstrip()
string.rstrip()

string = "aaaaabbbbbbaaaaa"
# 특정 문자 제거
# bbbbbb
string.strip("a") 
```