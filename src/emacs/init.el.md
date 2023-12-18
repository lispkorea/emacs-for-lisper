# init.el

Emacs가 시작될 때, 초기화 파일을 로드합니다. 초기화 파일은 `~/.emacs.el`, `~/.emacs`, `~/.emacs.d/init.el` 중 하나를 사용합니다.

| 파일명             |
| ------------------ |
| ~/.emacs.el        |
| ~/.emacs           |
| ~/.emacs.d/init.el |

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
# 예를들어 다른 위치에 있는 init.el을 로드하고 싶다면
emacs --no-init-file --load ~/other/init.el
```

- `.emacs.d/init.el`을 시작위치로, `.emacs.d/` 폴더를 github등을 이용해 버전관리해주면 좋습니다.
- `.org`파일로 `.el`를 생성할 수 있는 점을 이용. 문서화와 코드를 동시에 관리하는 방법도 있습니다.
  - 다만, 설정파일을 org로 다루는 것은 호불호가 갈리고, 무엇보다도 org를 다루기에는 너무나 방대합니다.
  - 따라서, **여기서 Org는 다루지 않겠습니다**.

## 참고

- [emacs: Init-File.html](https://www.gnu.org/software/emacs/manual/html_node/emacs/Init-File.html)
- [emacs: Find-Init.html](https://www.gnu.org/software/emacs/manual/html_node/emacs/Find-Init.html)

