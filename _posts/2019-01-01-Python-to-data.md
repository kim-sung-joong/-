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

```
    with open(filename) as file:
        for line in file:
            splited = line.split(",")
            word = splited[0]
            number = splited[1].strip()
            new_tuple=(word,number)
            tuples.append(new_tuple)
    return tuples
```

#### 튜플 형식으로 데이터를 저장하기 위해서는 데이터를 쌍으로 나누어 저장한다.
--------------------------------------------------------------------
```
books = []
    with open(src_file) as src:
        reader = csv.reader(src,delimiter=',')
        for row in reader:
            book = {
                "title": row[0],
                "author": row[1],
                "genre": row[2],
                "pages": int(row[3]),
                "publisher": row[4]
            }
            books.append(book)
    with open(dst_file, 'w') as dst:
        dst.write(json.dumps(books))
```

#### csv 데이터의 각 열은 고유한 의미를 가지기 때문에 각 열에 맞도록 데이터를 딕셔너리형식으로 리스트에 저장한다.
#### csv파일을 읽기 위한 함수 reader()
#### json파일 형식으로 저장하는 함수 load() , loads()는 스트링형식만 가능하다.
#### dumps()는 객체를 스트링형식으로 반환한다. dump()는 스트링형식이 아닌 파일형식.
###### csv 란 Comma-separated values의 약자로서 CSV 파일은 각 라인의 컬럼들이 콤마로 분리된 텍스트 파일 포맷이다.


