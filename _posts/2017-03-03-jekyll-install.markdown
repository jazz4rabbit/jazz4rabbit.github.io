---
layout: post
title:  "Github블로그와 Latex 적용"
date:   2017-03-03 22:26:00 +0900
categories: jekyll update
comments: true
---
# Github에 Blog 만들기, Latex 적용하기
학부때 수학과를 나왔는데 그때 Latex라는 것을 좀 사용한 적이 있었다. 배울때는(구글링..) 굉장히 이해하기 힘들었지만(아직도..) 그래도 내가 원하는 수식은 구글링하면 칠 수 있다. 수학과를 나와서 그런지 다른 문서(M사의 word나, 한글문서)의 수식은 눈에 거슬린다. Markdown에 Latex를 적용할 수 있다는 사이트를 찾아서 적용시켜보았다.

Latex을 사용하는 이유;

`$$ \displaystyle\sum_{k=1}^{n} k = \frac{n(n-1)}{2} $$`

$$ \displaystyle\sum_{k=1}^{n} k = \frac{n(n-1)}{2} $$


사이트는 다음을 참조하였다.(참조라기 보다 거의 붙여 넣었다...)

- [Github로 블로그 만들기 + LaTeX 적용하기][근본없는 개발자]

엄청난 시행착오를 겪었는데... 그래서 모든것을 기억하지 못한다... 설치한 운영체제는 macOS Sierra 10.12.3 이다.

# Github 가입하기
Github에서 Repository를 만드는데 이름을 [내 계정 이름].github.io 이어야 한다. 그리고 README.md를 자동으로 만들어준다.(만들지 않아도 상관은 없다.)

# Jekyll 설치하기
[Jekyll][]을 설치하자. 원래는 gem install jekyll 명령어인데 만일 되지않는다면 gem install jekyll -n /usr/local/bin 을 치도록 하자. (rm -rf /로 시스템 날리는 거 막으려고 애플이 도입한 SIP 때문이라고 한다) 만일 Bundler가 없다면 똑같은 방식으로 Bundler도 깔아주자.(gem install bundler)

# Jekyll 실행하기
원하는 디렉터리에 가서 `jekyll new [내 계정이름].github.io`을 치면 [계정이름].github.io 폴더가 생성된다.
터미널에
- `cd 계정이름.github.com`
- `jekyll serve --watch`

를 쳐주자. 그러면 뭔가 에러가 막 뜰 수 있는데, 디펜던시 걸린 패키지가 없다는 뜻이다. 이름 뜨는 거 잘 보고 해당하는 거 깔아주면 된다. 예를 들어 minima가 없다고 하면 `gem install minima -n /usr/local/bin`을 치면 해결이 될 것이다.

# Latex 연동하기(MathJax)
LaTeX을 설치할 예정이므로 필요 없는 사람은 블로그 만들기에 성공한 것이다.(아직 온라인에 등록이 안되었지만..) Jekyll에 [MathJax][]를 연동하면 수식을 입력할 수 있다고 한다. `_layouts/post.html` 의 <article> 태그 바로 다음 줄에 붙여넣으면 된다.
{% highlight html %}
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
{% endhighlight html %}

나는 설치했지만 `_layouts` 라는 폴더가 없었다. 사실 최신 버전의 Jekyll은 기본 테마로 [Minima][]를 쓰는데, 이걸 gem으로 관리한다고 한다. 위의 링크로 들어가서 Zip 파일을 받은 다음에 `_includes, _layouts, _sass, assets` 의 폴더를 페이지 설치한 디렉토리에 옮겨서 수정하면 된다.

# git 온라인 저장소에 연동하기(<a href="https://rogerdudler.github.io/git-guide/index.ko.html" target="\_blank"> 명령어 참조 </a>)
- `git init`    // .git 폴더가 생긴다.
- `git remote add origin remote-repository-url`   // origin에 주소를 등록한다?
- `git add .`     // 현재 폴더의 모든 파일들을 적재한다?(폴더포함)
- `git commit -m "Init BLOG"`   // commit 확정한다.(올릴파일을)
- `git push origin master`

remote-repository-url는 github의 원격 repo의 주소입니다. 보통 ```https://github.com/username/username.github.io.git``` (username을 자기아이디로 넣으면 됩니다.)

# 수식참조
LaTeX 문법은 스택 익스체인지의 한 스레드에 잘 정리되어 있어서, 참고하면 좋을 듯 하다.
<a href="http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference" target="\_blank"> stackexchange </a>

[근본없는 개발자]: https://helloworldpark.github.io/jekyll/update/2016/12/18/Github-and-Latex.html
[MathJax]: http://docs.mathjax.org/en/latest/start.html
[Minima]: https://github.com/jekyll/minima
[jekyll]: https://jekyllrb.com/
