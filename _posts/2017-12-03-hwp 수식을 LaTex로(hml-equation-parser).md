# hwp 수식을 LaTex로(hml-equation-parser)

수학 수식을 처리하는 방법이 항상 문제였는데 오픈 소스로 해결했다..
[관련기사](http://www.zdnet.co.kr/news/news_view.asp?artice_id=20161229092520), [github](https://github.com/OpenBapul/hml-equation-parser)

일단 이 패키지 작업 흐름은

1. hwp 파일을 hml 형식으로 변환해서 저장하기
2. 그 hml안의 수식을 LaTex화한 html 코드로 변환

이다.

## 작업 환경

[Cloud9 blank](http://c9.io)

## Installation

만약 `E: Unable to locate package` 이런 오류가 생길 수도 있으니 미리 update 시켜주자.[링크](https://community.c9.io/t/apt-get-install-unable-to-locate-packages/10561)

```shell
$ sudo apt-get update
```



그 다음 **hml-equation-parser** 패키지를 설치해야한다. 
하지만 주의해야 할 점이 있는데 

1. [**pandoc**](https://pandoc.org/installing.html)을 미리 설치해야 한다.
2. python3로 실행해야 한다. 
3. [**typing**](https://pypi.python.org/pypi/typing/3.6.2)이라는 파이썬 패키지를 미리 설치해야 한다. 

```shell
$ sudo apt-get install pandoc
$ sudo pip3 install typing
$ sudo pip3 install hml_equation_parser
```



성공적으로 설치했는지 확인해보자!

```shell
$ python3
>>> import hml_equation_parser as hp
>>> hp.eq2latex("LEFT ⌊ a+b RIGHT ⌋")
'\\left \\lfloor a+b \\right \\rfloor'
```
이렇게 나온다면 성공!!



예제 코드를 실행해보자!
hml 확장자를 가진 파일(ex. *test.hml*)을 준비하자.

*test.py*

```python
import hml_equation_parser as hp

doc = hp.parseHmlSample("test.hml")  # parse hml document and make ElementTree

doc = hp.convertEquationSample(doc)  # find equations from ElementTree and convert them to latex string
string = hp.extract2HtmlStrSample(doc)  # convert ElementTree to html document with MathJax.

import codecs

f = codecs.open("test.html", "w", "utf8")
f.write(string)
f.close()
```

*test.html*이 생성되면 성공이다.



 ## 주의점

1. 윈도우에서 안 된다. (코덱 인코딩 문제... 아직 해결 無)

2. `not supported tag` error가 있다.

   ```shell
   not supported tag: SECDEF
   not supported tag: COLDEF
   not supported tag: TABLE
   not supported tag: PICTURE
   ```

   ​