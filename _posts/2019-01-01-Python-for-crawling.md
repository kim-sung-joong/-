---
layout: post
title: 파이썬을 이용한 크롤링
category: Python
---
크롤링이란 ?

크롤링(crawling) 혹은 스크레이핑(scraping)은 웹 페이지를 그대로 가져와서 거기서 데이터를 추출해 내는 행위이다. 크롤링하는 소프트웨어는 크롤러(crawler)라고 부른다.
###출처(나무위키)

```import urllib.request
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


if __name__ == "__main__":
    main()
'''

