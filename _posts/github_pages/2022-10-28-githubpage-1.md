---
title : Github page 구성하기
date : 2022-10-28 15:30:00 +0900
categories : [ Github-pages ]
tags : [ github-pages, ruby ]
---

# Github-pages로 블로그 만들기

 다른 플랫폼을 사용하다 깃허브에서 호스팅 해주는 기능을 알게되서 사용하려 시도하다 귀찮음과 오류로 
 미루고 미루다 다시 해보려 합니다.

[github-pages](https://pages.github.com/)의 튜토리얼 문서를 참고 및 정리 하였습니다.

## 1. Create a Repository

 git repository를 사용하여 하는 것이니 repository를 하나 만들자

![저장소 생성](/assets/img/githubpage/github-pages-1.png)

저장소 이름을  `(내깃허브아이디).github.io` 사용하면 url을 그대로 사용할 수 있습니다.
그리고 따로 설정할 필요 없이 github-page 설정이 자동으로 설정되는것으로 보이는군요.

다른 이름으로 생성해도 이용 할 수 있습니다. 이후에 다른 설정이 필요 할 뿐이지요.

## 2. Set Page

 위에서 저장소명을 `(내깃허브아이디).github.io` 사용하면 자동으로 설정 되지만 임의로 만들었다면 설정을 해야할 수 있습니다.

깃허브 저장소 페이지에서 Setting - Page 로 들어가서 설정을 해주고

![저장소 설정](/assets/img/githubpage/github-pages-3.png)

`Github-pages`로 보여줄 `branch`를 선택해주면 되겠다.

![브랜치 설정](/assets/img/githubpage/github-pages-2.png)


## 확인하자!

`(내깃허브아이디).github.io` 또는 `(내깃허브아이디).github.io/(저장소명)` 으로 접속해보면
README.md 파일이 있다면 보여집니다!!!

![페이지 확인](/assets/img/githubpage/github-pages-4.png)

다음은 공식으로 지원하는 Jekyll를 사용하여 좀더 꾸며지는것을 도전해보겠습니다.




