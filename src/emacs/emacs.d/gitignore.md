# .gitignore

- [Emacs.gitignore](https://github.com/github/gitignore/blob/main/Global/Emacs.gitignore)


``` txt
*~                        : 백업파일
\#*\#                     :
/.emacs.desktop           : 
/.emacs.desktop.lock      :
*.elc                     : 컴파일(바이트) 파일
auto-save-list            : 자동저장 파일
tramp                     : tramp 관련
.\#*                      : 락파일

# Org-mode                : org-mode 관련
.org-id-locations
*_archive

# flymake-mode            : flymake 관련
*_flymake.*

# eshell files            : eshell 관련
/eshell/history
/eshell/lastdir

# elpa packages           : 패키지관련
/elpa/

# reftex files            : reftex 관련
*.rel

# AUCTeX auto folder      : AUCTeX 관련
/auto/

# cask packages           : cask 관련
.cask/
dist/

# Flycheck                : flycheck 관련
flycheck_*.el

# server auth directory   : emacsclient
/server/

# projectiles files       : projectile 관련
.projectile

# directory configuration : dir-locals
.dir-locals.el

# network security        : network-security 관련
/network-security.data

```

``` txt
# 컴파일(네이티브) 파일
/eln-cache/

# 캐쉬
/\.cache/

# 프로젝타일 관련
/projectile-bookmarks.eld
/projectile.cache

# 커스텀파일
/custom.el
```