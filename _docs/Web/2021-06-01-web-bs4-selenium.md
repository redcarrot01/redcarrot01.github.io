---
title: "BeautifulSoup4, Selenium"
category: Web
date: 2021-06-01 20:30:05
comments: true
order: 2
---



## 스크래핑 기초

#### HTTP 응답

클라가 웹서버(naver, google..)에 요청했을 때 서버는 HTML, CSS, JavaScript.. 로 응답

#### Dom(The Document Object Model) 문서

브라우저 위에 보이는 HTML 문자열을 Dom Tree로 변환하여 표현한다.

![image](https://user-images.githubusercontent.com/38436013/120283044-b981ce00-c2f5-11eb-8970-cde31df4d9db.png)

 <tbody>가 추가되었고, 나름의 DOM의 해석이다.

#### 왜 이렇게 하는가?

requests로 받은 응답은 서버가 최초로 응답하는 코드이며, 페이지 소스보기 코드 참고한다.  selenium 으로 받은 응답은 브라우저가 해석을 한 개발자 도구보기 코드 참고한다. 브라우저 해석을  DOM Tree라고 한다. 그 이유는 selenium은 브라우저를 통한 자동화이기때문이다. 

#### 파싱하는 방법

파싱 : HTML 문자열에서 내가 원하는 문자열 가져오기
1. 정규표현식이용
2. HTML Parser 라이브러리 : BeautifulSoup4 ..



## Requests

HTML 데이터 받아오는 라이브러리
requests로 데이터 받아와서 beautifulsoup으로 파싱해준다.
~~~python
import requests
~~~



## BeautifulSoup4

HTML 코드를 파이썬으로 사용하기 쉽게 parsing해주는 도구, 태그정보를 뽑아온다.

~~~python
from bs4 import BeautifulSoup 
html = '''
<ol>
    <li>NEVER - 국민의 아들</li>
    <li>SIGNAL - TWICE</li>
    <li>LONELY - 씨스타</li>
    <li>I LUV IT - PSY</li>
    <li>New Face - PSY</li>
</ol>
'''
soup = BeautifulSoup(html, 'html.parser')
for tag in soup.select('li'):
    print(tag.text)
~~~

#### 태그 정보 찾는 방법은 

1. find
2. 태그 관계 지정 css selector :    #이 id,   .이 class

#### 장점

간단하다. 정적페이지 스크래핑할 때 딱이다.

#### 단점

**자바스크립트로 만들어진 HTML -> 동적으로 생성된 정보는 가져올 수 없다!**

Ajax 형태로 통신하는 데이터가 많아졌는데, url변경이나 새로고침없이 데이터를 가져오므로 스크래핑이 실패함

> **Ajax(Asynchronous Javascript And XML)**
>
> > 자바스크립트 라이브러리 중 하나, 비동기식 자바스크립트와 xml의 약자
> >
> > 전체 페이지 고치지 않고, 일부만 데이터 로드하는 기법
> >
> > 자바스크립트를 사용한 비동기 통신, 클라이언트와 서버간에 XML 데이터를 주고받는 기술
> >
> > 자바스크립트를 통해 서버에 데이터 요청하는 것..
>
> **비동기 방식**
>
> > 웹페이지 리로드 하지 않고 데이터 가져오는 것
> >
> > 서버에 요청한 후 멈추는 것이 아니라 프로그램은 계속 돌아가는 것
>
> **동기 VS 비동기**
>
> > 동기 : 요청하면 결과가 주어질 때 까지 대기한다. 요청, 결과 동시에 일어난다
> >
> > 비동기 : 요청과 결과가 동시에 일어나지 않는다.



## Selenium

웹 브라우저를 자동화하는 도구로, 동적인 페이지 크롤링할 때 사용하는 라이브러리이다. 

Selenium을 사용하기 위해서는 먼저 selenium.webdriver 모듈을 import 한 후, webdriver.Chrome() 를 호출하여 브라우져를 실행시킨다. 브라우저 띄운 상태에서 특정 웹 사이트로 이동하기 위해 browser객체의 get()메서드를 사용한다.

~~~python
from selenium import webdriver
 
browser = webdriver.Firefox()
# browser = webdriver.Chrome()
 
browser.get("http://python.org")  
~~~

#### 동작

동적 페이지 크롤링 : selenium + webdriver

 selenium + webdriver 연동해서 크롤링하면, selenium은 가상 브라우저인 chrom web driver를 통해 웹서버 응답 받는다. selenium은 webdriver를 컨트롤할 수 있다.

#### 장점

자바스크립트가 동적으로 만든 데이터 크롤링할 때 사용
클릭, 키보드 입력 이벤트를 줄 때 사용

#### 단점

정말 느리다. 

#### 활용

자동 로그인
웹상 업무 자동화 : 메일 보내기, 좋아요 등등 

#### 데이터 찾는 방법은

1. find_elements_*()  ~

~~~python
from selenium import webdriver
import time
 
browser = webdriver.Firefox()
browser.get("http://python.org")
 
menus = browser.find_elements_by_css_selector('#top ul.menu li')
 
pypi = None
for m in menus:
    if m.text == "PyPI":
        pypi = m
    print(m.text)
 
pypi.click()  # 클릭
 
time.sleep(5) # 5초 대기
browser.quit() # 브라우저 종료
~~~



#### 참고했습니다.

https://greeksharifa.github.io/references/2020/10/30/python-selenium-usage/

https://www.hanumoka.net/2020/07/05/python-20200705-python-selenium-install-start/

https://velog.io/@surim014/AJAX%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80