---
title: Power Shell 꾸미기
date: 2022-02-03 00:00
categories: [etc]
tags: [windows, "power shell"]
# 기타 더 사용하는거 있으면 추가해놓기
---

개발을 하게 되면서 터미널을 자주 사용하게 되는데. MacOS, Linux는 oh-my-zsh 사용해서 많이 꾸민다.
단순 미관상뿐 아니라 생산성을 높일 수 있는 인터페이스로 꾸미기도 한다.
Windows도 PowerShell이라는 터미널을 사용하는데 비슷하게 꾸며서 사용하고 싶었다.

oh-my-posh를 이용해서 꾸며보자 아래는 공식문서를 따라한 내용이다.

- [oh-my-posh Windows 설치 페이지](https://ohmyposh.dev/docs/installation/windows)

---

## 1. Intall oh-my-posh

oh-my-zsh의 power shell 버전이라고 보면 되겠다. ( MacOS, Linux에서도 다 지원한다.) 관리자 모드로 power shell을 켜서 아래 명령어를 입력해주자.

```cmd
winget install JanDeDobbeleer.OhMyPosh -s winget
```

## 2. Font 설치

꾸며지는테마에서 사용되는 아이콘등이 깨지지 않기 위해서는 권장하는 폰트를 설치하는것이 좋겠다. 별도로 권장하는 폰트를 받아 설치해도 가능하고 아래 방법으로 진행해도 도 되겠다.  
 설치 후 oh-my-posh 설치후 아래 명령어를 입력하면 되겠다.

```cmd
oh-my-posh font install
```

입력하면 설치 할 수 있는 폰트목록이 나온다. 공식문서에서는 Meslo LGM NF 폰트를 추천한다. Meslo를 찾아서 설치해주자. ( 물론 다른 폰트를 사용해도 된다 그럴경우 아이콘등이 지원하지 않아 minimal 버전의 테마를 사용하라고 한다. )
![설치 터미널 이미지](/assets/img/etc/font_install.png)

## 3. 테마 적용

이제 대망의 테마 적용이다.
간단하다. 아래명령어를 이용하여 적용하면된다.

```bash
oh-my-posh init pwsh --config [설정경로]
```

설정경로에 테마 경로를 입력하면 된다. 이떄 로컬에 json파일을 받아서 지정해도 되고
URL을 입력해도 된다. 로컬에 받는경우 아래 명령어를 입력시에 일관적으로 테마를 다운받아준다.

```cmd
Get-PoshThemes
```

ex)

```cmd
oh-my-posh init pwsh --config 'https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/agnoster.omp.json' | Invoke-Expression
```

영구적으로 적용이 안될시에는 프로필설정?에 위 명령어를 추가해서 저장해주면 된다.

ex) 아래명령어 입력후

```cmd
notepad $PROFILE
```

메모장에 `oh-my-posh init pwsh --config 'https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/agnoster.omp.json' | Invoke-Expression`
입력후 저장

---

적용후 모습!!

![명령프롬프트](/assets/img/etc/prompt_theme.png)
