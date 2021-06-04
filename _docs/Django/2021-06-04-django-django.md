---
title: "django 특징"
category: Django
date: 2021-06-04 11:15:05
comments: true
order: 1
---



#### 1. Django 

파이썬 기반의 웹 프레임워크로, 웹 프레임 워크의 장점인 반복적인 기능을 구현되어 있다. 로그인, 회원가입, 인증, CORS, data parsing 등 라이브러리를 이용해 간단하게 사용할 수 있다.  

**MVT vs MVC**

장고는 MVT패턴을 사용한다. 스프링은 MVC 패턴이다.

- Model(Model) : 데이터에 관한 정보를 다루는 컴포넌트다.
- View(Template) : 실제로 화면을 보여주는 인터페이스
- Controller(View) : Model과 Template를 연결해주는 역할이다. urls.py에서 넘어온 요청을 토대로 model에서 데이터를 읽어와 작업을 수행한 후, template에서 html 파일을 가져와 render 후 사용자에게 넘겨준다.

#### 2. 사용자의 요청이  Django API까지 도달하는 과정

<img src="https://user-images.githubusercontent.com/38436013/120792564-ad557500-c570-11eb-93c1-380e99a81f3c.png" alt="image" style="zoom:67%;" />

웹서버에 요청 오면 장고로 전달된다. 장고는 url을 분석하고, 해당 요청을 view(함수)에 넘겨준다.

데이터는 Model을 참고하여 읽어오고, 비지니스 로직은 view에서 처리된다. template에서 html을 읽어와서 브라우저에 응답한다.

#### 3. Django의 ORM

**ORM(Object Relational Mapping)**

- 객체와 관계형 DB(Relational Database)의 데이터를 매핑해주는 것 : 객체지향은 프로그래밍은 객체를 사용하고, DB는 테이블을 사용하는데, 두 모델 간 불일치가 있고 이것을 ORM을 통해 해결할 수 있다.
- SQL을 자동 생성하여 쿼리문 없이도 DB 다룰 수 있다.
- Java : Hibernate, jpa / Python : Django ORM , SQLAlchemy 

예를 들면,
SQL 쿼리 사용시, 쿼리문 작성과 데이터 가져오는 일련의 모든 과정들을 코드 작성해야한다.

~~~python
book_list = new list();
sql = "SELECT book FROM library WHERE author = 'ychaen' ";
data = query(sql);
while(row = data.next()){
	book = new Book();
	book.setAuthor(row.get('author'));
	book_list.add(book);
}
~~~

반면 ORM을 사용하면, 간단하게 표현가능하다.

~~~python
book_list = BookTable.query(author="ychaen")
~~~

**ORM 장점**

- 코드 작성 적어서 생산성 좋다.  코드 재사용 가능해진다. -> 객체지향적이다.
- DBMS에 대한 의존성, 종속성이 줄어든다.

**ORM 단점**

- ORM 만으로 완벽한 서비스 구현은 어렵다. 
- 잘못 구현되는 경우에 속도 저하, 일관성이 무너지므로 설계에 신중해야 한다.
- 일부 대형 쿼리는 SQL을 통해 유지 보수한다. (별도의 구현)

**QuerySets**

- 전달받은 모델의 객체 목록, 데이터베이스의 여러 레코드를 나타낸다.
- 쿼리셋은 데이터베이스로부터 데이터 읽고, 필터를 걸거나 정렬할 수 있다. DB에 영향 주지 않는다.
- 쿼리셋을 순회하는 시점에, 쿼리셋에 해당하는 DB의 레코드들을 실제로 가져오며 이는 모두 Django 모델로 변환된다.

#### 참고했습니다.
- [https://mungto.tistory.com/302](https://mungto.tistory.com/302)
- [https://changrea.io/jpa/orm/](https://changrea.io/jpa/orm/)
- [https://ychae-leah.tistory.com/137?category=340269](https://ychae-leah.tistory.com/137?category=340269)
- [https://velog.io/@suasue/Django-ORM%EA%B3%BC-QuerySet](https://velog.io/@suasue/Django-ORM%EA%B3%BC-QuerySet)