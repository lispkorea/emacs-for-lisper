# .gitignore

- [template: .gitignore](https://github.com/lispkorea/template-emacs.d/blob/main/.gitignore)
- [Emacs.gitignore](https://github.com/github/gitignore/blob/main/Global/Emacs.gitignore)


``` txt
# -*- mode: gitignore; -*-
## here: https://github.com/lispkorea/template-emacs.d/blob/main/.gitignore
## ref: https://github.com/github/gitignore/blob/main/Global/Emacs.gitignore

# 이맥스 ============================================================

## 임시파일
*~

## 락(lock)파일
#*

## 컴파일(네이티브)
/eln-cache/
.eln

## 컴파일(바이트)
.elc

## 캐쉬
/\.cache/

## 기타
/eln-cache/

# 자동저장 파일
auto-save-list

## 디렉토리 설정
.dir-locals.el

## 데스크탑
/.emacs.desktop
/.emacs.desktop.lock

## 커스텀파일
/custom.el

## reftex files
*.rel

## AUCTeX auto folder
/auto/

## server auth directory
/server/

## network security
/network-security.data


# 라이브러리 ============================================================

## 라이브러리 - package
/elpa/

## 라이브러리 - eshell
/eshell/

## 라이브러리 - projectile
/projectile-bookmarks.eld
/projectile.cache
/projects

## 라이브러리 - ido
/ido.last

## 라이브러리 - elisp-autofmt
/elisp-autofmt-cache/

## 라이브러리 - flycheck
flycheck_*.el

## 라이브러리 - flymake-mode
*_flymake.*

## 라이브러리 - lang-racket
/racket-mode/

## 라이브러리 - ido
/ido.last

## 라이브러리 - tramp
tramp

## 라이브러리 - org
.org-id-locations
*_archive

## 라이브러리 - amx
/amx-items

## 라이브러리 - multiple-cursors
/.mc-lists.el

## 라이브러리 - magit
/transient/

# 기타 ============================================================

## 임시파일(MacOs)
.DS_Store

## cask packages
.cask/
dist/
```