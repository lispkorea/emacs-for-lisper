# base-setting.el

## 설정

- 예전에는 `file-name-coding-system`, `set-terminal-coding-system`, `set-keyboard-coding-system` 등등 했었은데 이제는 `set-default-coding-systems` 하나로 끝낸다.
- 예전에는 [(defalias 'yes-or-no-p 'y-or-n-p)](https://www.gnu.org/software/emacs/manual/html_node/elisp/Yes_002dor_002dNo-Queries.html) 이런식으로 했었다

``` lisp
;; file: base-setting.el

(progn ;; `설정::한글'
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Language-Environments.html
  (set-language-environment "Korean"))

(progn ;; `설정::utf-8'
  ;; utf-8 설정
  ;; ref: https://www.masteringemacs.org/article/working-coding-systems-unicode-emacs
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/elisp/Default-Coding-Systems.html
  (set-default-coding-systems 'utf-8)
  (prefer-coding-system 'utf-8))

(progn ;; `설정::Y_혹은_N으로_대답'
  (setq read-answer-short t)
  (setq use-short-answers t))


(progn ;; `설정::인덴트'
  (setq-default indent-tabs-mode nil)
  (setq tab-width 4))

(use-package delsel
  ;; ref: https://github.com/emacs-mirror/emacs/blob/master/lisp/delsel.el
  :ensure nil
  :config
  (delete-selection-mode +1))

(use-package whitespace
  :ensure nil
  :hook (before-save . whitespace-cleanup))


```