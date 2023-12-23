# emacs.d/

- [이곳](https://github.com/lispkorea/template-emacs.d)에서 미리 설정한 `.emacs.d/` 템플릿을 받을 수 있습니다.

Emacs가 시작될 때, 초기화 파일을 로드합니다.

| 파일명                  |                       |
| ----------------------- | --------------------- |
| ~/.emacs.el             | 안쓰는게 좋음.        |
| ~/.emacs                | 안쓰는게 좋음.        |
| ~/.emacs.d/init.el      | Windows, macOs에 추천 |
| ~/.config/emacs/init.el | Linux에 추천          |

- 변수 `user-emacs-directory`는 초기화 파일이 있는 폴더 명시합니다.
  - ex) "~/.emacs.d/"

Emacs는 다음과 같은 시작 옵션을 제공합니다.

| emacs 옵션                    | 설명                               |
| ----------------------------- | ---------------------------------- |
| --no-init-file / -q           | 기본 초기화 파일을 로드하지 않음   |
| --debug-init                  | 초기화 파일에 디버거를 활성화 시킴 |
| --load 파일위치 / -l 파일위치 | 특정 파일을 로드함                 |
| --no-window-system / -nw      | GUI를 사용하지 않음                |
| --init-directory=폴더         | init 폴더를 지정한 곳으로 설정가능 |


```bash
# init폴더 영향 없이 다른 위치에 있는 elisp만 로드
emacs --no-init-file --load ~/other/init.el

# 다른 위치에 있는 init 폴더로 초기화 하며 이맥스를 켜고 싶다면.
# --init-directory 옵션은 29.1 버전부터 지원
emacs --init-directory=~/other_init_dir
```

- `.emacs.d/init.el`을 시작위치로, `.emacs.d/` 폴더를 github등을 이용해 버전관리해주면 좋습니다.
- `.org`파일로 `.el`를 생성할 수 있는 점을 이용. 문서화와 코드를 동시에 관리하는 방법도 있습니다.
  - 다만, 설정파일을 org로 다루는 것은 호불호가 갈리고, 무엇보다도 org를 다루기에는 너무나 방대합니다.
  - 따라서, **여기서 Org는 다루지 않겠습니다**.

## emacs.d

설명하기 편하게 시작폴더를 `~/.emacs.d/`로 가정하겠습니다.

- `~/.emacs.d/.gitignore`를 만들어 줍니다.
  - [Emacs.gitignore](https://github.com/github/gitignore/blob/main/Global/Emacs.gitignore)를 다운로드 받아서 `~/.emacs.d/.gitignore`에 저장합니다.
