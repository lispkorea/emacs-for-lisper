# early-init.el

- `~/.emacs.d/early-init.el`은 다음과 같은 일을 할 것입니다.
  - GUI 로드되기 전 설정

|                    |                                                                                   |
| ------------------ | --------------------------------------------------------------------------------- |
| gc-cons-threshold  | GC가 발생되는 바이트 수 설정                                                      |
| gc-cons-percentage | gc-cons-threshold를 바탕으로 percentage가 초과되면 GC가 발생 - 기본값 0.1. 즉 10% |

GUI가 로드되기 전에 설정됨으로, menu-bar, tool-bar와 같이 안쓰는 것이 있다면, 이 단계에서 제거해주는 것이 좋습니다.

``` lisp
(setq gc-cons-threshold most-positive-fixnum)
(setq gc-cons-percentage 0.6)
(add-hook 'emacs-startup-hook
          (lambda ()
            (setq gc-cons-threshold (* 16 1024 1024)))
            (setq gc-cons-percentage 0.1))


(push '(menu-bar-lines . 0) default-frame-alist)
(push '(tool-bar-lines . 0) default-frame-alist)
(push '(vertical-scroll-bars) default-frame-alist)
```