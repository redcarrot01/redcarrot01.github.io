---
title: "Linux 기본 명령어"
category: Linux
date: 2021-06-02 09:56:05
comments: true
order: 1
---



#### 명령어 종류 요약입니다.

아래는 자주 쓰는 명령어만 간단하게 정리했으므로, 자세히 알고 싶다면, 맨 아래의 '[참고했습니다](http://throughkim.kr/2017/01/09/linux-14/#%ED%97%B7%EA%B0%88%EB%A6%AC%EB%8A%94-%EB%82%B4%EC%9A%A9)' 에 링크를 확인해 주세요.

> **파일 시스템**
> ls , chown, chmod, du, df, free, cat dd, rm, mount, ln, tar, touch, mkdir  
> **검색**  
> find, grep  
> **프로세스**  
> at, cron, kill, nice, ps, top  
> **네트워크**   
> netstat, nslookup, ssh, iptables  
> **텍스트 처리**   
> awk, cut, head/tail, sed, more, vi, wc, split, sort  
> **그 외**   
> usermod, 모듈   
> **패키지 관리자**   
> yum, rpm, apt-get

#### 새로운 파일을 만드는 방법

vi newfile : vi 편집기 상태로 들어감  
touch newfile : 빈 파일만 생성됨  
cat > newfile : vi 편집기 상태로 들어감, 문서 작성 후 ctrl +D로 빠져나옴

#### 파일 내용만 보기

cat filename : 파일의 내용을 모두 보여줌  
head -n filename : n줄 만큼 위에서부터 보여줌  
tail -n filename : n줄 만큼 아래에서부터 보여줌   

#### mv : 파일 이름(rename)/ 위치(move) 변경

mv index.htm index.html : index.htm 파일을 index.html로 이름 변경  
mv file ../main/new_file : 파일 위치 변경  

#### mkdir : 디렉토리 생성

mkdir download  

#### rm : 파일 삭제

rm test.html : test.html 파일 삭제  
rm -r <디렉토리> : 디렉토리 전체 삭제  
rm -i a.* : a로 시작하는 모든 파일 삭제할 것인지 일일이 확인하면서 삭제

#### rmdir : 디렉토리 삭제

rmdir cgi-bin : cgi-bin 디렉토리 삭제

#### ls : 파일 리스트 보기

ls -l : 포맷, 소유자, 용량, 날짜 등 정보를 함께 보여줌  
ls -F : 파일의 형태를 나타내는 문자 추가하여 출력, 폴더는 '/', 링크는 '@'  
ls -a : 숨김 파일을 포함한 모든 파일 출력  
ls -R : 서브디렉토리 재귀 출력  
ls -t : 수정시간에 따라 파일 목록 나열  
ls -C : 한 줄에 여러 개의 정보를 표시

#### cd : 디렉토리 변경

cd cgi-bin : cgi-bin 하부 디렉토리로 들어감  
cd .. : 상위 디렉토리 이동  
cd / cd~ : 홈 디렉토리 이동  
cd /webker : 다른 디렉토리 이동하려면 '/' 사용  

#### pwd : 현재의 디렉토리 경로를 보여줌

#### cat : 파일의 내용을 화면에 출력하거나 파일을 만드는 명령

cat filename

#### find : 각종 파일/디렉토리 검색하기

find -name '*.pl' : 현재 디렉토리에서 pl확장자 가진 모든 파일 검색   
find / -name '*.pl' : 루트에서부터 pl 확장자를 가진 모든 파일 검색  
find / -name 'ab*' : 루트에서부터 파일명이 ab로 시작하는 모든 파일 검색  
find / -name 'et*' -type d : 루트에서부터 디렉토리 이름이 et로 시작하는 모든 디렉토리 검색  


#### grep : 파일 내에서 지정한 패턴이나 문자열 검색

- 사용법 : grep [ -옵션 ] [ 패턴 ] [ 파일명 ]

- 옵션 
	-c : 패턴이 일치하는 행의 수를 출력  
    -i : 비교시 대소문자 구별 안함  
    -v : 지정한 패턴과 일치하지 않는 행만 출력  
    -n : 행의 번호 함께 출력  
    -l : 패턴이 포함된 파일의 이름을 출력  
    -w : 패턴이 전체 단어와 일치하는 행만 출력 

- 파일에서 문자열 찾기

    - grep "문자열" [파일이름] : 파일 하나에서 찾기    
    - grep "문자열1\|문자열2" [파일이름] : 두가지 문자열 찾기    
    - grep "문자열" [파일이름] [파일이름] : 파일 여러개에서 찾기


- 정규표현식
![image](https://user-images.githubusercontent.com/38436013/120405607-e7155880-c383-11eb-8048-5ce0a89a9b0f.png)

## 그 외 파일 시스템 명령어

#### chown(change the owner of a file) : 소유권 바꾸기

chown prankster file1 : file1 파일의 소유자를 prankster로 수정  
chown user1:user2 file2 : file2 파일의 소유자를 user1로 그룹을 user2로 수정  
chown -cR nobody:nobody dir : dir 폴더와 그안의 모든 파일,디렉토리의 소유자,소유그룹 변경

#### chmod : 접근 권한 바꾸기

chmod o+rw a_file : others에게 읽기, 쓰기 권한을 추가(+)한다.   
chmod o-x test : test 파일에, 나머지 사용자(o)의 실행(x) 권한을 제거(-)한다.   
chmod ugo+rx a_file : user, group, others에 읽기, 쓰기 권한을 추가한다   
chmod u+x,g+rw,o-r test : user에게 쓰기 권한을 추가하고, group에게 읽기,쓰기 권한을 추가하고, others에게 읽기 권한을 제거한다.

     0 = --- = 0+0+0
     1 = --x = 0+0+1
     2 = -w- = 0+2+0
     3 = -wx = 0+2+1
     4 = r-- = 4+0+0
     5 = r-x = 4+0+1
     6 = rw- = 4+2+0
     7 = rwx = 4+2+1  

chmod 755 a_file : 소유자에겐 7(rwx), 그룹과 나머지에겐 5(r-x) 권한부여  
chmod 700 * : 현재 위치의 모든 파일과 폴더 권한 수정      

chmod -R 654 test :  -R : 하위 디렉토리와 파일의 권한까지 변경

#### cron : 반복적인 예약 작업 수행해주는 데몬

~~~
*   *   *   *   *  수행할 명령어
┬   ┬   ┬   ┬   ┬
│   │   │   │   │
│   │   │   │   │
│   │   │   │   └───────── 요일 (0 - 6) (0 =일요일)
│   │   │   └────────── 월 (1 - 12)
│   │   └─────────── 일 (1 - 31)
│   └──────────── 시 (0 - 23)
└───────────── 분 (0 - 59)
~~~


#### 참고했습니다.[
[http://throughkim.kr/2017/01/09/linux-14/#grep](http://throughkim.kr/2017/01/09/linux-14/#grep)
[http://ivis.kr/images/e/e9/2018_Unix_command_vi.pdf](http://ivis.kr/images/e/e9/2018_Unix_command_vi.pdf)

[https://wiseworld.tistory.com/97](https://wiseworld.tistory.com/97)

