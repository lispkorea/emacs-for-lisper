# os-macos.el

- <https://www.gnu.org/software/emacs/manual/html_node/elisp/Window-Systems.html>
- 맥의 커맨드키를 이맥스의 메타키로 사용하는게 편하다.

``` lisp
;; file: os-macos.el

(when (eq system-type 'darwin)
  ;; `설정::macOs'

  ;;
  ;; ns : NeXTSTEP. Darwin이전에 사용되던 OS
  ;; darwin: Darwin (kernel)로 macOs의 기반이되는 코어.
  ;; darwin/ns/mac 이라 치면 보통 macOs구나 라고 생각하면 편하다.
  ;; mac-function-modifier => alias ns-function-modifier
  ;;
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Mac-_002f-GNUstep-Customization.html
  ;;
  ;; +-----+-------+-----+-----+-------------------+-----+-----+
  ;; |     |       |     |     |                   |     |     |
  ;; |Fn   |Ctrl   |Optn |Cmd  |       Space       |Cmd  |Optn |
  ;; +-----+-------+-----+-----+-------------------+-----+-----+
  ;; |hyper|control|super|meta |       Space       |Cmd  |Optn |
  ;; +-----+-------+-----+-----+-------------------+-----+-----+
  ;;
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Mac-_002f-GNUstep-Customization.html
  (setq ns-function-modifier 'hyper)
  (setq ns-control-modifier 'control)
  (setq ns-option-modifier 'super)
  (setq ns-command-modifier 'meta)
  ;; (global-set-key (kbd "S-x") 'kill-region)
  ;; (global-set-key (kbd "S-c") 'kill-ring-save)
  ;; (global-set-key (kbd "S-v") 'yank)
  ;; (global-set-key (kbd "S-a") 'mark-whole-buffer)
  ;; (global-set-key (kbd "S-s") 'save-buffer)
  ;; (global-set-key (kbd "S-z") 'undo)
  ;; (global-set-key (kbd "S-+") 'text-scale-adjust)
  ;; (global-set-key (kbd "S--") 'text-scale-adjust)
  )
```