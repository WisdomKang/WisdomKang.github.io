---
title : Github page 배포 오류
date : 2024-01-26 00:00:00 +0900
categories : [ Github-pages ]
tags : [ github-pages, error ]
---

# GithubPage 배포 오류

 오랜만에 포스팅을 올려봤는데 github page에서 build시에 에러가 났다.
 기존에 문제발생했을때는 글을 쓸때 사용하는 markdown파일의 양식이 다르면 오류가 잘 안되던거 였는데 이번에는 다시 쓸글을 지우고 틀린 부분을 비교해도 되지 않았다.


github 페이지 Action 탭에 있는 workflow에 남겨져 있는 log를 확인해보았다.

```
In Gemfile:
  jekyll-theme-chirpy was resolved to 5.6.1, which depends on
    jekyll-archives was resolved to 2.2.1, which depends on
      jekyll was resolved to 4.3.3, which depends on
        jekyll-sass-converter was resolved to 3.0.0, which depends on
          sass-embedded was resolved to 1.70.0, which depends on
            google-protobuf
Error: The process '/opt/hostedtoolcache/Ruby/3.3.0/x64/bin/bundle' failed with exit code 5
```

Ruby를 모르고 사용하기에 부정확하지만 의존성 문제라고 하는거 같다. Chatgpt로 질문 해봤지만 답변해준 해결책으로는 해결 되지 않았다.
좀 더 구글링으로 비슷한 error log를 찾았다.

해결법...

github/workflows/pages-deploy.yml 파일을 수정해 주었다.
디렉토리명만 봐도 배포시 동작에 관여하는 파일이라 보였다. 아무튼 여기서 ruby의 버전을 설정해주면 된다.

```yml
...
ruby-version: 3.2
...
```

기존에는 "ruby-version: 3" 이였는데 이렇게 변경하니 오류없이 빌드 되었다. 버전에 관련된 문제였던것 같다. 검색하면서 ruby 3.3 integration?? 관련 이슈들이 보였는데 이글 작성 시점보다 3개월 전 문제라 해결이 된건지 아니면 앞으로 해결된건지 알아보고 지켜봐야겠다.

너무 오랜만에 사용하니 사용법도 잊어버리고 버전호환문제가 생겨도 대응도 잘 못하고 github page를 사용하는것 자체도 이런 관리하는 법에 대하여 공부를 하게되니 글도 자주 써보고 공부하고 정리하는것도 버릇을 잘 들여봐야겠다.

끝.