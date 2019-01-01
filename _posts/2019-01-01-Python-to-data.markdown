---
layout: post
title:  "Python to data"
categories: Python
---

```
corpus = 'corpus.txt'
def print_lines(filename):
    '''
    파일의 내용을 줄 번호와 한 줄씩 출력합니다
    >>> print_lines(corpus)
    1 zoo,768
    2 zones,1168
    3 zone,2553
    '''
    line_number = 1
    contents = []
    with open(filename,'r') as file:
        for line in file:
            contents.append(line)
            print(str(line_number)+" "+str(contents[line_number-1]))
            line_number += 1
```

--------------------------------
```
with open(filename,'r') as file:
        for line in file:
```
#### open()을 이용하면 지정한 파일 이름에 해당하는 파일을 열고, 읽거나 수정가능.
#### with...as 을 사용하면 파일을 자동으로 닫을 수 있음.
#### for문을 이용하여 1줄씩 line에 받아오기.
