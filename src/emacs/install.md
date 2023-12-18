# Emacs 설치

emacs 컴파일 옵션이 여러가지가 있으며, 아래 명령어를 통해 확인할 수 있습니다.

``` sh
# ref: https://emacs.stackexchange.com/a/35512
emacs -nw -q --batch --eval '(message system-configuration-options)'
```

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
sudo apt-get install git
```

### 스냅 설정

- [snap](https://snapcraft.io/)
  - <https://snapcraft.io/emacs>

``` sh
sudo apt install snapd
sudo snap install emacs --classic
sudo snap remove
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
# ref: https://gist.github.com/wisedier/3f9ebfa376ebfc31165a

sudo apt-get install language-pack-ko
sudo apt-get install language-pack-ko-base
sudo apt-get install localepurge

# /etc/default/locale
# /etc/environment
# /etc/profile

sudo echo "ko_KR.EUC-KR EUC-KR" >> /var/lib/locales/supported.d/ko
sudo locale-gen --purge
sudo dpkg-reconfigure locales
sudo echo 'LANG="ko_KR.UTF-8"' >> /etc/environment
sudo echo 'LANG="ko_KR.UTF-8"' >> /etc/profile
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

# font 설치
brew tap homebrew/cask-fonts
brew install font-d2coding-nerd-font
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

