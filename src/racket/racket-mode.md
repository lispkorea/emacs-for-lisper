# Racket Mode

- [메뉴얼](https://racket-mode.com/)
  - [명령어](https://racket-mode.com/#Commands)
- [소스](https://github.com/greghendershott/racket-mode)
- ref
  - <https://www.linw1995.com/en/blog/Write-Racket-With-Emacs/>

| 기능          | 단축키  | 설명                       |
| ------------- | ------- | -------------------------- |
| 자동완성      | C-M-i   | complete-symbol            |
| repl 접속     | C-c C-k | racket-run-module-at-point |
| repl 접속     | C-c C-c | racket-run-module-at-point |
| 폼(form) 평가 | C-M-x   | racket-send-definition     |

## 설정

``` lisp
;; ref: https://racket-mode.com/
;; command: https://racket-mode.com/#Commands

;; C-M-i        complete-symbol
;; C-c C-k      racket-run-module-at-point
;; C-c C-c      racket-run-module-at-point
;; C-M-x        racket-send-definition
(use-package racket-mode
  :ensure t
  :config
  (require 'racket-xp)
  (add-hook 'racket-mode-hook #'racket-xp-mode))
```