# Emacs 설치


## Windows

- [scoop](https://scoop.sh/)

``` powershell
# scoop 설치
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression

## git과 emacs 설치
scoop bucket add extras
scoop update
scoop install git
scoop install emacs

# 기타 유틸들
scoop install ag direnv fzf global openssh ripgrep gow fd gpg
```

- 기타
  - [TortoiseGit](https://tortoisegit.org)
  - [Git For Windows](https://gitforwindows.org/)
  - [Rapid Environment Editor](https://www.rapidee.com/en/about)
- 간혹 운영체제 호환성 문제로 인해 윈도우에서 WSL을 이용하여 우분투를 사용하는 경우가 있습니다.
  - [WSL을 사용하는 경우](https://lispkorea.github.io/etc/wsl/)

## Linux

``` sh
# 기본적으로 git은 설치하자
sudo apt-get install git

# 기본 저장소의 emacs의 버전이 낮아 지워주자
sudo apt autoremove --purge emacs

# 최신 emacs빌드를 설치하기 위해 새로운 저장소를 추가해주고
sudo add-apt-repository ppa:kelleyk/emacs
sudo apt update && sudo apt upgrade

# emacs를 설치하자
sudo apt-get install emacs28

# 아래 명령어는 추후 지울때 사용
sudo apt autoremove --purge emacs28
sudo add-apt-repository --remove ppa:kelleyk/emacs
```

## macOs

- <https://emacsformacosx.com/>

``` sh
# homebrew 설치
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# git 설치
brew install git

# emacs 설치
brew install --cask emacs
```
