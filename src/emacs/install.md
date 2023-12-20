# Emacs 설치

emacs 컴파일 옵션이 여러가지가 있으며, 아래 명령어를 통해 확인할 수 있습니다.

- 설치
  - [windows](#windows)
  - [linux](#linux)
  - [macOs](#macos)
- 폰트
  - [D2Coding 고정폭 폰트](https://github.com/naver/d2codingfont)

``` sh
# ref: https://emacs.stackexchange.com/a/35512
# 설치된 emacs의 컴파일 옵션 확인
emacs --no-window-system --no-init-file --batch --eval "(message system-configuration-options)"
```

## Windows

- [scoop](https://scoop.sh/)

``` powershell
# scoop 설치
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression

## git과 emacs 설치
scoop bucket add extras
scoop install emacs
scoop bucket add main
scoop install git

# 윈도우10에서는 BSD Tar가 설치되어 있음. 하지만 필요한건 GNU Tar
scoop bucket add main
scoop install tar

# 기타 유틸들
scoop bucket add main
scoop install ripgrep
scoop install direnv
scoop install fzf
scoop install global
scoop install openssh
scoop install gow
scoop install fd
scoop install gpg
```

- 기타
  - 깃
    - [TortoiseGit](https://tortoisegit.org)
    - [Git For Windows](https://gitforwindows.org/)
  - 환경변수
    - [Rapid Environment Editor](https://www.rapidee.com/en/about)
- 간혹 운영체제 호환성 문제로 인해 윈도우에서 WSL을 이용하여 우분투를 사용하는 경우가 있습니다.
  - [WSL을 사용하는 경우](https://lispkorea.github.io/etc/wsl/)

## Linux

``` sh
sudo apt update

# 기본적으로 git은 설치하자
sudo apt-get install -y git
```

### 스냅 설정

- [snap](https://snapcraft.io/)
  - <https://snapcraft.io/emacs>

``` sh
sudo apt install -y snapd
sudo snap install -y emacs --classic

# 삭제시
# sudo snap remove
```

| [모드](https://snapcraft.io/docs/install-modes) | 설명                                                  |
| ----------------------------------------------- | ----------------------------------------------------- |
| --classic                                       | classic confinement for full system access            |
| --dangerous                                     | dangerous mode for testing local unsigned snaps       |
| --devmode                                       | developer mode for testing and viewing log output     |
| --jailmode                                      | forces a snap to be installed with strict confinement |

| [채널](https://snapcraft.io/docs/channels) | 설명                                                                                          |
| ------------------------------------------ | --------------------------------------------------------------------------------------------- |
| --beta                                     | for users wanting to test the latest features, typically outside of a production environment. |
| --edge                                     | for users wanting to closely track development.                                               |



### 한글 설정

``` sh
# /etc/default/locale
# /etc/environment
# /etc/profile

# 언어팩 설치
sudo apt-get install -y language-pack-ko
sudo apt-get install -y language-pack-ko-base
sudo apt-get install -y localepurge


sudo echo "ko_KR.EUC-KR EUC-KR" >> /var/lib/locales/supported.d/ko
sudo locale-gen --purge
sudo dpkg-reconfigure locales
sudo echo 'LANG="ko_KR.UTF-8"' >> /etc/environment
sudo echo 'LANG="ko_KR.UTF-8"' >> /etc/profile

# 고정폭 폰트 설치
sudo apt-get install -y fonts-naver-d2coding 
```

|                       |                           |
| --------------------- | ------------------------- |
| /usr/share/fonts/     | fonts for all users       |
| ~/.local/share/fonts/ | fonts for particular user |

``` sh
# fc-cache : 폰트 빌드
fc-cache  --force --verbose

# fc-list : 폰트 목록 확인
fc-list

# fc-query : 폰트 정보 확인
# download: https://raw.githubusercontent.com/kelvinks/D2Coding_Nerd/master/D2Coding%20v.1.3.2%20Nerd%20Font%20Complete.ttf
fc-query ./D2Coding%20v.1.3.2%20Nerd%20Font%20Complete.ttf | grep family
```

## macOs

- brew
  - <https://formulae.brew.sh/formula/emacs>
    - `brew install emacs`
  - <https://formulae.brew.sh/cask/emacs>
    - <https://emacsformacosx.com/>
      - `brew install --cask emacs`

``` sh
# homebrew 설치
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# git 설치
brew install git
# gnu-tar 설치
brew install gnu-tar

# font 설치
brew tap homebrew/cask-fonts
brew install font-d2coding-nerd-font

# 기타 유틸들
brew install ripgrep
```

``` sh
# emacs 설치
brew install --cask emacs
```

### 좀 더 옵션을 자유롭게 넣고 싶다

- <https://github.com/d12frosted/homebrew-emacs-plus>
  - `--with-native-comp` 옵션이 있는 homebrew-emacs-plus로 선택

``` sh
# emacs 설치
brew tap d12frosted/emacs-plus
# for Just-In-Time Compilation
# ref: https://gcc.gnu.org/wiki/JIT
brew install libgccjit
export CC=gcc
brew install emacs-plus@29 --with-native-comp 
# Emacs.app was installed to:
#   /opt/homebrew/opt/emacs-plus@29
#
# To link the application to default Homebrew App location:
#   ln -s /opt/homebrew/opt/emacs-plus@29/Emacs.app /Applications
#
# Your PATH value was injected into Emacs.app/Contents/Info.plist
#
# Report any issues to http://github.com/d12frosted/homebrew-emacs-plus
#
# To start d12frosted/emacs-plus/emacs-plus@29 now and restart at login:
#   brew services start d12frosted/emacs-plus/emacs-plus@29
# Or, if you don't want/need a background service you can just run:
#   /opt/homebrew/opt/emacs-plus@29/bin/emacs --fg-daemon

ln -s /opt/homebrew/opt/emacs-plus@29/Emacs.app /Applications
```

### macOs 락스크린 방지


- `Control-Command-Q` : 화면 잠금 단축키가 할당되어 있다.
- lisp-mode에선 `C-M-q`가 `indent-pp-sexp`로 할당되어 있다.
  - `indent-pp-sexp`: 괄호로 묶여 있는 모든 줄을 재정렬한다.
- 자주 쓰는 기능인데 단축키가 겹쳐 화면 잠금 단축키를 덮어 씌우는 편이 좋다.
  - ` > 하단에보면 > 화면 잠금`이 있는데 이걸 다른키로 맵핑 시킬 것이다.
  - ` > 시스템 설정 > 키보드 > 키보드 단축키... > 앱 단축키 > 모든 응용 프로그램 >  +`
    - `메뉴 제목`에 `화면 잠금`을 입력한다. ( 눌러서 이름/띄어쓰기가 동일한지 확인)
    - 원하는 단축키를 입력한다.


## Ref

- <https://github.com/syl20bnr/spacemacs>