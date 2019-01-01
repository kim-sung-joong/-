---
layout: post
title: 파이썬을 이용한 크롤링
category: Python
---
## 크롤링이란 ?

#### 크롤링(crawling) 혹은 스크레이핑(scraping)은 웹 페이지를 그대로 가져와서 거기서 데이터를 추출해 내는 행위이다. 크롤링하는 소프트웨어는 크롤러(crawler)라고 부른다.

###### 출처(나무위키)
--------------------------------------
```
import urllib.request
from bs4 import BeautifulSoup
def main():
    url = "http://www.newsis.com/eco/list/?cid=10400&scid=10404"
    req = urllib.request.Request(url)
    sourcecode = urllib.request.urlopen(url).read()
    soup = BeautifulSoup(sourcecode, "html.parser")
    for text in soup.find_all("strong",class_="title"):
        num = text.get_text().find("…")
        if num!=-1:
            print(text.get_text()[:num])
        else:
            print(text.get_text())
```
---------------------------------------
```
import urllib.request
```

#### urllib는 URL 작업을 위한 여러 모듈을 모은 패키지다.
1. urllib.request : URL을 열고 읽기 위함.
2. urllib.error : request에 의해 발생하는 예외를 포함.
3. urllib.parse : URL 구문 분석을 위함.
4. urllib.robotparser : robots.txt을 분석하기 위함.

###### robots.txt 파일은 검색 엔진 크롤러에서 사이트에 요청할 수 있거나 요청할 수 없는 페이지 또는 파일을 크롤러에 지시하는 파일입니다.
-----------------------------------------

```
from bs4 import BeautifulSoup
```

#### request로 받은 html을 python이 이해하는 객체 구조로 만들어주는 라이브러리.

-----------------------------------------
```
for text in soup.find_all("strong",class_="title"):
```

#### soup객체에서 찾고 싶은 class를 추출한다.





