# 다양한 패키지

## 기본

- [cl-lib](https://www.gnu.org/software/emacs/manual/html_mono/cl.html)
  - Common Lisp emulation package
- [compat](https://github.com/emacs-compat/compat)
  - COMPATibility Library for Emacs Lisp
- [eieio(`E`nhanced `I`mplementation of `E`macs `I`nterpreted `O`bjects)](https://www.gnu.org/software/emacs/manual/html_node/eieio/)
  - common lisp의 CLOS를 참고하여 만든 객체 시스템
  - 이전 버전의 Emacs와의 하위 호환성을 깨지 않고, 개발중인 패키지에서 최신 API에 접근할 수 있도록 해줌.

## etc

- [nerd-icons](https://github.com/rainstormstudio/nerd-icons.el)
  - `M-x nerd-icons-install-fonts` => Symbols Nerd Fonts Mono
  - NFM.ttf
  - third-party
    - [nerd-icons-ivy-rich](https://github.com/seagle0128/nerd-icons-ivy-rich)
    - [nerd-icons-ibuffer](https://github.com/seagle0128/nerd-icons-ibuffer)
    - [nerd-icons-completion](https://github.com/rainstormstudio/nerd-icons-completion)
    - [nerd-icons-corfu](https://github.com/LuigiPiucco/nerd-icons-corfu)

https://github.com/rolandwalker/simpleclip


https://blog.shiren.dev/2017-11-13-%EC%9D%B4%EB%A7%A5%EC%8A%A4%EC%99%80-%ED%95%A8%EA%BB%98%ED%95%98%EB%8A%94-%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD/

swiper
avy
iedit
wgrep
multi-term
which-key

elpa
use-package
fly-check
helm
projectile
company
paredit
yasnippet
centaur-tabs
magit

hydra https://github.com/abo-abo/hydra

treemacs

키보드 > 텍스트입력 > 편집 > 문서의 입력 소스로 자동전환 체크
Automatic switch to a document's input source

(when (eq system-type 'darwin)
  (setq mac-command-modifier 'meta))

theme
color-theme-sanityinc-tomorrow

* 패키지 및 설정을 더 편리하게 할 수 있는 [use-package](https://github.com/jwiegley/use-package)

* 중첨된 괄호를 다른 색으로 표시해주는 [rainbow-delimiters](https://github.com/Fanael/rainbow-delimiters)


https://unipro.tistory.com/226


editorconfig
https://github.com/editorconfig/editorconfig-emacs

기본 문서화
markdown
ref: https://qiita.com/howking/items/bcc4e05bfb16777747fa
ref: https://jblevins.org/projects/markdown-mode/

mermaid
https://github.com/abrochard/mermaid-mode
ref: https://qiita.com/hotoku/items/e05c75d899754731660f
ref: https://github.com/hotoku/fosi

## completion

- ref
  - https://blog.tomoya.dev/posts/a-new-wave-has-arrived-at-emacs/

| 패키지 이름                                                               |      | 해설                                                                                                                                                |
| ------------------------------------------------------------------------- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Vertico](https://github.com/minad/vertico)                               | 2021 | Emacs 표준의 보완 후보( *Completion*버퍼에 표시되는 아레)와 완전한 호환성을 가지는 것을 목표로 만들어진 보완 UI 패키지.                             |
| [selectrum](https://github.com/radian-software/selectrum)                 | 2019 | (deprecated) vertico사용 권유. Swiper와 비슷한 UI로, Emacs 표준의 보완 API를 이용하면서, 기능 확장을 목표로 한 보완 UI 패키지.                      |
| [iv](https://github.com/abo-abo/swiper#ivy)                               | 2013 | 보완 후보의 표시에 미니 버퍼를 활용한 최초의 보완 UI 패키지. Ivy/Counsel 를 위해 만들어졌다.                                                        |
| [ido](https://www.gnu.org/software/emacs/manual/html_node/ido/index.html) | 2013 |                                                                                                                                                     |
| [helm](https://github.com/emacs-helm/helm)                                | 2012 | Anything의 포크로 탄생. 많은 플러그인이 만들어져 보수적인 Anything에 대해 파괴적 변경을 넣어도 성장을 우선했다.                                     |
| [anything](https://github.com/emacs-jp/anything)                          | 2007 | 인크리멘탈 보완의 편리함을 널리 세상에 알린 기념해야 할 최초의 프레임워크. 창을 분할하여 보완 후보를 표시합니다. 모든 것은 여기에서 시작되었습니다. |

- [company](https://github.com/company-mode/company-mode) 
  - company "just" does code/text autocompletion and a few related things like docstring lookup
- [helm](https://github.com/emacs-helm/helm)
  - Emacs incremental completion and selection narrowing framework
- [Ivy](https://github.com/abo-abo/swiper?tab=readme-ov-file#ivy)
  - a generic completion mechanism for Emacs.
  - 필터링

 Company-mode is a package for in-buffer code completion,
 while Helm/Ivy are general narrowing-completion frameworks. 
 Helm/Ivy will turn that action into a narrowing completion list. 
corfu https://github.com/minad/corfu
 🏝️ corfu.el - COmpletion in Region FUnction 

 https://github.com/clemera/helm-ido-like-guide
 https://github.com/creichert/ido-vertical-mode.el


minibuffer

| fuzzy matching                              |                                                 |
| ------------------------------------------- | ----------------------------------------------- |
| [fussy](https://github.com/jojojames/fussy) | Emacs completion-style leveraging flx           |
| [flx](https://github.com/lewang/flx)        | Fuzzy matching for Emacs ... a la Sublime Text. |



 
 

https://qiita.com/takaxp/items/2fde2c119e419713342b


## Common Lisp
[slime](../commonlisp/slime.md)
[sly](../commonlisp/sly.md)
## Racket
## Clojure
cider
clojure-mode
## Emacs

etags
gtags https://www.gnu.org/software/global/
ctags https://ctags.io/
rtags https://github.com/Andersbakken/rtags