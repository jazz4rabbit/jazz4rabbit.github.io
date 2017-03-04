---
layout: post
title:  "Anaconda에 Tensorflow 설치하기(windows 10)"
date:   2017-03-04 17:00:00 +0900
categories: tensorflow
---
Tensorflow 를 설치한 운영체제는 windows 10에 설치하였다.

# 요약
급한 사람들을 위해!!

[anaocnda](https://www.continuum.io/downloads) 설치

anaconda prompt 열기 (아래의 명령어 실행)

{% highlight sh linenos %}
conda update conda
conda update anaconda
conda create -n tensorflow python=3.5 anaconda
activate tensorflow
conda install -c conda-forge tensorflow
{% endhighlight %}

# Anaconda install
[anaocnda](https://www.continuum.io/downloads) 홈페이지에서 3.6 version으로 다운받았다. (2.7 version으로 다운받아도 상관없다. 어차피 아나콘다 가상환경으로 다시 설치할것이므로 그때 버전을 선택할 수 있다.)

![Anaconda install]({{ site.url }}/Resources/IMG/anaconda_install.png)

# Anaconda update
이 과정은 실행하지 않아도 상관은 아마 없을 것이다.
Anaconda Prompt를 열어서 다음의 명령어를 입력해주자.

- `conda update conda`
- `conda update anaconda`

# Anaconda virtual environments 생성하기
Anaconda에는 가상환경이라는 것이 존재하는데 패키지 같은것이 꼬일 수 있기때문에 가상환경 별로 따로 패키지 설치가 가능하다.
명령어는 [conda github](https://conda.io/docs/using/envs.html)에서 자세히 나와있다. (전부 있지는 않다.)

다음과 같이 가상환경을 생성할 수 있다. name 에는 가상 환경을 부르고 싶은 이름을 넣으면 되고, x.x 에는 사용하고자 하는 파이썬 버전을 넣어주면 된다.
- `conda create -n name python=x.x anaconda`

나의 경우 아래와 같이 tensorflow 라는 이름으로 파이썬 3.5 를 사용하는 가상 환경을 만들었다.

 `conda create -n tensorflow python=3.5 anaconda`

# Anaconda virtual environments 활성화 / 비활성화
 - `activate name` // 활성화 하고 싶은 name을 입력한다.
 - `deactivate`    // 활성화 되있는 가상환경을 해제한다.

 가상환경에 tensorflow를 설치할 것이므로 위에서 만든 가상환경을 활성화 해주자.

 나의 경우 `activate tensorflow
 `를 입력했다.

# Tensorflow 설치하기
[Tensorflow 공식문서](https://www.tensorflow.org/install/install_windows)를 따라하면 설치가 안된다...

[구글](http://stackoverflow.com/questions/37130489/installing-tensorflow-with-anaconda-in-windows)에 자문을 구했더니 해결책이 있었다.

`conda install -c conda-forge tensorflow`

설치가 완료된다. `jupyter notebook` 명령어를 입력하여서 tensorflow가 잘 설치되었는지 확인해보자.

다음의 명령어를 입력하자.

{% highlight python %}
import tensorflow as tf

hello = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
print(sess.run(hello))
{% endhighlight %}

`Hello, TensorFlow!`가 나온다면 잘 설치된 것이다!!
