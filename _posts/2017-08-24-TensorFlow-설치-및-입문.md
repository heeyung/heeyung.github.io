---
layout: post
title: TensorFlow 설치 및 입문
category: tensorflow
---

# TensorFlow 설치 및 입문

## 소개

텐서플로우는 기계 학습과 딥러닝을 위해 구글에서 만든 오픈소스 라이브러리입니다. 데이터 플로우 그래프 방식을 사용합니다.

#### 데이터 플로우 그래프

데이터 플로우 그래프는 수학 계산과 데이터의 흐름을 노드와 엣지를 사용한 방향 그래프로 표현합니다.

#### 특징

텐서플로우는 다음과 같은 특징을 가집니다:

- 데이터 플로우 그래프를 통한 풍부한 표현력
- 코드 수정 없이 CPU/GPU 모드로 동작
- 아이디어 테스트에서 서비스 단계까지 이용 가능
- 계산 구조와 목표 함수만 정의하면 자동으로 미분 계산을 처리
- Python/C++를 지원하며, [SWIG](http://www.swig.org/)를 통해 다양한 언어 지원 가능

> "구글이 텐서플로우를 오픈소스로 한 것은, 기계 학습이 앞으로 제품과 기술을 혁신하는데 가장 필수적인 요소라고 믿기 때문입니다." - Google Brain Team

## 설치

제약 조건:

- Unix계열 OS(Linux/Mac OCX)만 지원합니다.
- GPU 버전은 Linux만 지원합니다.

#### Linux / Mac OCX

Unix 계열 OS를 사용하시는 분들은 [설치 문서](https://www.tensorflow.org/install/)를 참고하세요.

#### 윈도우

윈도우 사용자는 가상 머신을 이용하거나, [도커 툴박스 설치](https://docs.docker.com/docker-for-windows/) 후 진행하시기 바랍니다.

#### 이미지를 받고 컨테이너 실행

텐서플로우의 도커 이미지는 소스코드, 예제, 툴도 포함되어 있기에 풀 버전을 받는 것을 권합니다.

**Linux/Mac OCX**

```shell
docker run -it b.gcr.io/tensorflow/tensorflow-full
```

UNIX 계열 OS에서는 위의 명령을 실행하면 이미지를 받고 컨테이너가 실행됩니다. 컨테이너 실행 후 자동으로 컨테이너 안의 쉘 환경으로 들어가게 됩니다.

컨테이너 안의 `/tensorflow`폴더에 소스가 설치되어 있습니다.(주의: 이 폴더에서 모듈을 import 하시면 error가 발생합니다.)

**윈도우**

윈도우의 경우 Docker QuickStart Terminal 실행 후(이때 고래 그림 아래의 IP를 기억해둡니다.) 아래와 같이 실행하시기 바랍니다.

```shell
winpty docker run -it -p 8888:8888 b.gcr.io/tensorflow/tensorflow-full
```

이미지를 받은 후 컨테이너가 실행되면, Jupyter 노트북 서버가 자동으로 시작된 상태입니다. 웹브라우저에서 '위의IP:8888'을 입력하면 Jupyter Notebook 환경에 접속됩니다. 여기에서 tensorflow를 사용할 수 있습니다.

**동작 확인**

설치가 잘 되었는지 다음의 코드로 확인해봅니다.

```shell
$ python
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print sess.run(hello)
Hello, TensorFlow!
>>> a = tf.constant(10)
>>> b = tf.constant(32)
>>> print sess.run(a+b)
42
>>>
```

## 기본 개념 익히기

일단 기본 용어부터 살펴보겠습니다.

#### 용어

**오퍼레이션(Operation)**

그래프 상의 노드는 오퍼레이션(op)으로 불립니다. 오퍼레이션은 하나 이상의 텐서를 받을 수 있습니다. 오퍼레이션은 계산을 수행하고, 결과를 하나 이상의 텐서로 반환할 수 있습니다.

**텐서(Tensor)**

내부적으로 모든 데이터는 텐서를 통해 표현됩니다. 텐서는 일종의 다차원 배열인데, 그래프 내의 오퍼레이션 간에는 텐서만이 전달됩니다.

**세션(Session)**

그래프를 실행하기 위해서는 `세션` 객체가 필요합니다. 세션은 오퍼레이션의 실행 환경을 캡슐화한 것입니다.

**변수(Variables)**

변수는 그래프의 실행시, 패러미터를 저장하고 갱신하는데 사용됩니다. 메모리 상에서 텐서를 저장하는 버퍼 역활을 합니다.

#### 예제

간단한 예제를 통해 기본 개념을 확인하겠습니다.

```python
import tesorflow as tf

# 변수를 0으로 초기화
state = tf.variable(0, name="counter")

# state에 1을 더할 오퍼레이션 생성
one = tf.constant(1)
new_value = tf.add(state, one)
update = tf.assign(state, new_value)

#그래프는 처음에 변수를 초기화해야 합니다. 아래 함수를 통해 init 오퍼레이션을 만듭니다.
init_op = tf.initialize_all_variables()

# 그래프를 띄우고 오퍼레이션들을 실행
with tf.Session() as sess:
  # 초기화 오퍼레이션 실행
  sess.run(init_op)
  # state의 초기 값을 출력
  print(sess.run(state))
  # state를 갱신하는 오퍼레이션을 실행하고, state를 출력
  for _ in range(3):
    sess.run(update)
    print(sess.run(state))
```

결과

```
0
1
2
3
```

## reference

[텐서플로우 시작하기](https://gist.github.com/haje01/202ac276bace4b25dd3f)

