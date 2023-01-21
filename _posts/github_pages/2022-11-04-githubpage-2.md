---
title : Github page Jekyll 사용하기
date : 2022-11-04 00:00:00 +0900
categories : [ Github-pages ]
tags : [ github-pages, ruby, jekyll ]
---

# Github-pages Jekyll 사용하여 꾸미기!
이전에 단순 깃허브에 올린 repository를 웹페이지로 호스팅해주는 것을 해보았습니다.
이번에는 다른 블로그처럼 각 페이지를 꾸며보겠습니다.

[github-pages docs](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll) 공식 문서를 참고 하여 작성하였습니다.


## Jekyll란?
 먼저 [jekyll](https://jekyllrb.com/)란 정적 사이트를 만들어주는 빌드 프로세스라고 설명하고 있습니다. 제가 사용하는 부문만을 보고 쉽게 풀면
markdown 같은 파일 형식을 읽어서 webpage에 보여 줄 수있는 html 페이지로 만들어주는 빌드툴 정도로 이해하고 있습니다.

## Installation 
필요한 도구를 설치하겠습니다.

- Ruby  : jekyll 구현한 언어?
- jekyll 
- bundler   : ruby 기반 프로젝트 패키지매니져?

위 두개를 설치해 줍니다.

[Ruby](https://www.ruby-lang.org/en/documentation/installation/)는 홈페이지에서 받아서 설치.

다음 gem을 사용하여 jekyll, bundler를 설치해 줍니다.

```shell
$ gem install bundler jekyll
```

이러면 로컬에서 테스트 하기 위한 준비는 대략 됐습니다!

## Theme 사용하기

 기본명령어로 템플릿 프로젝트를 만들고 하면 시간 걸리니 바로 필요한 테마를 적용하는 것으로 넘어가겠습니다!

다른 개발자들이 멋들어지게 만들어놓은 테마를 일단 찾아야합니다.

- [Jekyll Themes](http://jekyllthemes.org/)
- [Free Jekyll themes](https://jekyllthemes.io/free)
등등 검색해보면 쉽게 찾을 수 있을겁니다.

제가 적용한것은 [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/)라는 테마입니다.
기본적이고 간단한게 아주 마음에 드는군요. 여러 기능도 들어있지만...;; 여기까지만...

### 적용하기
 적용하는 법은 README를 따라서 시키는데로 하면 되는데...
 지금 사용하려는 테마는 start template을 만들어 제공하고 있습니다.


[chirpy-starter](https://github.com/cotes2020/chirpy-starter/generate) 링크를 이용 저장소를 복사해서 이용 또는
기존 github-pages repository에 복사하여 넣어주면 됩니다.

그후 _config.yml 파일을 수정해줍니다.

```yml
...
baseurl: '/{경로명}'                # [사용자명].github.io를 사용하고 있다면 안해도 됩니다.
timezone: Asia/Seoul                # 타임존 설정
url: 'https://wisdomkang.github.io' # 뒤 경로는 제외하고 수정해주면 됩니다.
...
```

그외에 설정은 문서를 잘 읽어보고 필요한부분을 수정하면 되겠습니다. 저는 기본적인 사항만 수정했습니다.

설정이 완료 되고 repository에 commit, push 하면 끝!

이후 github저장소의 Action에 가면 진행상황을 확인 할 수 있습니다.

![Action페이지](/assets/img/githubpage/github-pages-5.png)

'pages buildand  deployment' 보이시죠? jekyll 프로젝트를 빌드하는 메세지를 확인 할 수 있습니다.

됐다면 현제 블로그 처럼 보이게 됩니다!

---

기억 나는데로 적었는데 ... 뭔가 시원찮습니다.
보기좋게 이해하기 쉽게 적는게 쉽지 않네요...