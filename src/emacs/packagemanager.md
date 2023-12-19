# 패키지 관리자

- [package.el 소스](https://github.com/emacs-mirror/emacs/blob/master/lisp/emacs-lisp/package.el)
  - Emacs 24부터(2012년 6월) 내장

| M-x                      |     |
| ------------------------ | --- |
| package-list-packages    |     |
| package-initialize       |     |
| package-refresh-contents |     |
| package-install 패키지명 |     |

``` lisp
(require 'package)
(setq package-user-dir "~/.emacs.d/__package")
(setq package-check-signature nil)
(setq package-archives
      '(
        ;; official - gnu
        ("gnu" . "https://elpa.gnu.org/packages/")

        ;; officiral - melpa
        ("melpa" . "http://melpa.org/packages/")
        ("melpa-stable" . "http://stable.melpa.org/packages/")

        ;; 이하 미러는 기호에 맞게 추가
        ;; mirror - melpa mirrorservice
        ("melpa" . "http://www.mirrorservice.org/sites/melpa.org/packages/")
        ("melpa-stable" . "http://www.mirrorservice.org/sites/stable.melpa.org/packages/")

        ;; mirror - melpa 중국
        ("melpa" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/melpa/")
        ("melpa-stable" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/melpa-stable/")
        ))
(package-initialize)
```

## 패키지 설정

- [use-package](https://github.com/jwiegley/use-package)
  - A use-package declaration for simplifying your .emacs 
  - 29.1부터 기본 탑재
- [el-get](https://github.com/dimitri/el-get)
  - Manage the external elisp bits and pieces upon which you depend!
- [leaf.el](https://github.com/conao3/leaf.el)
  - Flexible, declarative, and modern init.el package configuration 
- [straight.el](https://github.com/radian-software/straight.el)
- [elpaca](https://github.com/progfolio/elpaca)
  - Elpaca는 심볼릭 링크가 필수

## 설정

- [init-loader](https://github.com/emacs-jp/init-loader)
