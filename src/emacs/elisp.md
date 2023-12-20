# elisp

- [메뉴얼](https://www.gnu.org/software/emacs/manual/elisp.html)
- [스타일가이드](https://github.com/bbatsov/emacs-lisp-style-guide)
- [emacsdocs: elisp](https://emacsdocs.org/docs/elisp/Emacs-Lisp)

## ielm

IELM(`I`nteractive `E`macs `L`isp `M`ode)

`M-x ielm RET`

### 기타 유용한 함수

| 기능      | 단축키 | 함수              |
| --------- | ------ | ----------------- |
| 코드 평가 | M-`:`  | eval-expression   |
| 모드확인  |        | describe-mode     |
| 변수설명  |        | describe-variable |
| 함수설명  |        | describe-function |

| .el 파일에서                      | 단축키 | 함수           |
| --------------------------------- | ------ | -------------- |
| form 평가                         | C-M-x  | eval-defun     |
| 괄호로 묶여 있는 모든 줄을 재정렬 | C-M-q  | indent-pp-sexp |

## 컴파일

- [바이트 컴파일](https://www.gnu.org/software/emacs/manual/html_node/eintr/Byte-Compiling.html)
- [네이티브 컴파일](https://www.gnu.org/software/emacs/manual/html_node/elisp/Native_002dCompilation-Functions.html)

| 확장자 | 설명            |
| ------ | --------------- |
| .el    | 텍스트          |
| .elc   | 바이트 컴파일   |
| .elf   | 네이티브 컴파일 |

- 참조: <https://www.grugrut.net/posts/202104272222/>


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
  (when (eq system-type 'darwin)
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
    ))
```

## 기타

``` lisp
;; association list
;; push를 사용하게 되면 같은 키가 여러개 생긴다.
(defvar x-alist '((a . 1)))       ; ((a . 1))
(push '(a . 1) x-alist)           ; ((a . 1) (a . 1))
;; add-to-list를 사용하면 같은 키가 여러개 생기지 않는다.
(defvar x-alist '((a . 1)))       ; ((a . 1))
(add-to-list 'x-alist '(a . 1))   ; ((a . 1))
(add-to-list 'x-alist '(a . 2))   ; ((a . 1) (a . 2)) ;; 의도하지 않은 결과가 나온다.
;; ref: https://stackoverflow.com/a/25100962

;; property list
(defvar x-plist '(:a 1 :b 2))     ; (:a 1 :b 2)
(plist-get x-plist :b)            ; 2


;; 사전
;; ref: https://www.gnu.org/software/emacs/manual/html_node/elisp/Dictionaries.html
;; memq
> (memq 9 '(1 2 3))
nil
> (memq 2 '(1 2 3))
(2 3)
```