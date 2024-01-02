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

| 확장자 | 설명             |
| ------ | ---------------- |
| .el    | 텍스트           |
| .elc   | 컴파일(바이트)   |
| .eln   | 컴파일(네이티브) |

- 참조: <https://www.grugrut.net/posts/202104272222/>

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

eq
eql
equal

set
setq

defvar
defconst

memq
meml
member

## 참고

- [ElispCheatSheet](https://github.com/alhassy/ElispCheatSheet)
- <https://tuhdo.github.io/emacs-for-proglang.html>
- <https://tuhdo.github.io/helm-intro.html>