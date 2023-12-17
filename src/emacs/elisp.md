# elisp

- [메뉴얼](https://www.gnu.org/software/emacs/manual/elisp.html)


## ielm

IELM(`I`nteractive `E`macs `L`isp `M`ode)

| 기능   | 단축키   |
| ------ | -------- |
| 구동   | M-x ielm |
| 도움말 | C-h m    |

## 컴파일

- [바이트 컴파일](https://www.gnu.org/software/emacs/manual/html_node/eintr/Byte-Compiling.html)
- [네이티브 컴파일](https://www.gnu.org/software/emacs/manual/html_node/elisp/Native_002dCompilation-Functions.html)

| 확장자 | 설명            |
| ------ | --------------- |
| .el    | 텍스트          |
| .elc   | 바이트 컴파일   |
| .elf   | 네이티브 컴파일 |


## 설정


``` lisp
(progn ; `설정::한글'
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Language-Environments.html
  (set-language-environment "Korean"))
```

``` lisp
(progn ; `설정::utf-8'
  ;; utf-8 설정
  ;; ref: https://www.masteringemacs.org/article/working-coding-systems-unicode-emacs
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/elisp/Default-Coding-Systems.html
  (set-default-coding-systems 'utf-8))
```
예전에는 `file-name-coding-system`, `set-terminal-coding-system`, `set-keyboard-coding-system` 등등 했었은데 이제는 `set-default-coding-systems` 하나로 끝낸다.

``` lisp
(progn ; `설정::Y_혹은_N으로_대답'
  (setq read-answer-short t)
  (setq use-short-answers t))
```
예전에는 [(defalias 'yes-or-no-p 'y-or-n-p)](https://www.gnu.org/software/emacs/manual/html_node/elisp/Yes_002dor_002dNo-Queries.html) 이런식으로 했었다



## 맥 전용 옵션

``` lisp
(progn ; `설정::macOs'
  ;; ref: https://qiita.com/takashihattori/items/9ebc57bb5a68f0c87e35
  (when (equal window-system 'mac)
    (setq mac-function-modifier 'meta)
    (setq mac-option-modifier 'meta)
    (setq mac-command-modifier 'super)
    ;; (global-set-key (kbd "s-x") 'kill-region)
    ;; (global-set-key (kbd "s-c") 'kill-ring-save)
    ;; (global-set-key (kbd "s-v") 'yank)
    ;; (global-set-key (kbd "s-a") 'mark-whole-buffer)
    ;; (global-set-key (kbd "s-s") 'save-buffer)
    ;; (global-set-key (kbd "s-z") 'undo)
    ;; (global-set-key (kbd "s-+") 'text-scale-adjust)
    ;; (global-set-key (kbd "s--") 'text-scale-adjust)
    ))
```