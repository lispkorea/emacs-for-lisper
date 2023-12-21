# init.el

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

## init.el

설명하기 편하게 시작폴더를 `~/.emacs.d/`로 가정하겠습니다.

- `~/.emacs.d/init.el`에는 다음과 같은 일을 할 것입니다.
  - `package.el`와 `use-package`를 이용해 패키지를 받을 저장소를 지정합니다.
  - `init-loader`를 이용해 초기화 파일을 관리합니다.

## package

- [Package Manager](packagemanager.md) 참고
  - package.el: Emacs 24.1(2012-06-10)
  - use-package: Emacs 29.1(2023-07-30)
- Package Archive
  - elpa(`E`macs `L`isp `P`ackage `A`rchive)
  - melpa(`M`ilkypostman `E`macs `L`isp `P`ackage `A`rchive)
- 미러
  - [미러: 칸트대학](https://www.mirrorservice.org/)
  - [미러: 칭화대학](https://mirrors.tuna.tsinghua.edu.cn/help/elpa/)

``` lisp
(use-package package
  ;; 
  ;; ref: https://github.com/emacs-mirror/emacs/blob/master/lisp/emacs-lisp/package.el
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Packages.html
  ;; 
  ;; elpa(`E`macs `L`isp `P`ackage `A`rchive)
  ;; melpa(`M`ilkypostman `E`macs `L`isp `P`ackage `A`rchive)
  ;; 
  ;; elpa(gnu): https://elpa.gnu.org/
  ;; elpa(nognu): https://elpa.nongnu.org/
  ;; melpa: http://melpa.org/
  ;; melpa(stable): http://stable.melpa.org/
  ;; 미러 칸트대학: https://www.mirrorservice.org/
  ;; 미러 칭화대학: https://mirrors.tuna.tsinghua.edu.cn/help/elpa/
  :config
  (progn ;; `elpa'
    (defconst PACKAGE_ELPA_GNU
      '("gnu" . "https://elpa.gnu.org/packages/"))
    (defconst PACKAGE_ELPA_NOGNU
      '("nongnu" . "https://elpa.nongnu.org/nongnu/")))
  (progn ;; `melpa'
    (defconst PACKAGE_MELPA
      '("melpa" . "http://melpa.org/packages/"))
    (defconst PACKAGE_MELPA_STABLE
      '("melpa-stable" . "http://stable.melpa.org/packages/")))
  (progn ;; `mirrorservice'
    (defconst PACKAGE_MIRRORSERVICE_MELPA
      '("melpa" . "http://www.mirrorservice.org/sites/melpa.org/packages/"))
    (defconst PACKAGE_MIRRORSERVICE_MELPA_STABLE
      '("melpa-stable" . "http://www.mirrorservice.org/sites/stable.melpa.org/packages/")))
  (progn ;; `tsinghua'
    (defconst PACKAGE_TSINGHUA_GNU
      '("gnu" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/gnu/"))
    (defconst PACKAGE_TSINGHUA_NOGNU
      '("nognu" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/nongnu/"))
    (defconst PACKAGE_TSINGHUA_MELPA
      '("melpa-cn" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/melpa/"))
    (defconst PACKAGE_TSINGHUA_MELPA_STABLE
      '("melpa-stable-cn" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/stable-melpa/")))

  (setq package-archives
	`(,PACKAGE_TSINGHUA_GNU
	  ,PACKAGE_TSINGHUA_NOGNU
	  ,PACKAGE_TSINGHUA_MELPA
	  ,PACKAGE_TSINGHUA_MELPA_STABLE
          )))
```

## init-loader

- [emacs-jp/init-loader](https://github.com/emacs-jp/init-loader/)

| elisp                 | 설명                    |
| --------------------- | ----------------------- |
| init-loader-directory | 초기화 파일이 있는 폴더 |

``` lisp
(use-package init-loader
  :ensure t
  :init
  (let* ((my-inits-dir (concat user-emacs-directory "inits")))
    (unless (file-exists-p my-inits-dir)
      (make-directory my-inits-dir t))
    (setq init-loader-directory my-inits-dir))
  ;; (setq init-loader-byte-compile t)
  (init-loader-load))
```

## 참고

- [emacs: Init-File.html](https://www.gnu.org/software/emacs/manual/html_node/emacs/Init-File.html)
- [emacs: Find-Init.html](https://www.gnu.org/software/emacs/manual/html_node/emacs/Find-Init.html)
