# Slime

SLIME(`S`uperior `L`isp `I`nteraction `M`ode for `E`macs)

- [홈페이지](https://slime.common-lisp.dev/)
- [저장소](https://github.com/slime/slime)

| 분류 | 단축키  | 내용                   | 함수                                     |
| ---- | ------- | ---------------------- | ---------------------------------------- |
| 평가 |         |                        |                                          |
|      | C-M-x   | 현재 폼 평가           | slime-eval-defun                         |
|      | C-c C-l | 파일 로드              | slime-load-file                          |
|      | C-c ~   | REPL 네임스페이스 설정 | slime-sync-package-and-default-directory |
| 이동 |         |                        |                                          |
|      | M-.     | 정의로 이동            | slime-edit-definition                    |
|      | M-,     | 되돌아가기             | slime-pop-find-definition-stack          |
|      | C-c C-z | REPL로 이동            | slime-repl                               |

## 설정

``` lisp
(use-package slime
  :ensure t
  :init
  (setq inferior-lisp-program (executable-find "sbcl"))
  (setq slime-contribs '(slime-asdf
                         slime-fancy
                         slime-indentation
                         slime-sbcl-exts
                         slime-scratch))
  (setq slime-complete-symbol-function 'slime-fuzzy-complete-symbol)
  (setq slime-net-coding-system 'utf-8-unix)
  (define-key slime-mode-map (kbd "C-c M-n") 'slime-sync-package-and-default-directory)
  ;; slime-lisp-implementations
  ;; common-lisp-hyperspec-root
  ;; common-lisp-hyperspec-symbol-table
  ;; common-lisp-hyperspec-issuex-table
  )
```

아래는 `eros`를 이용해서 오버레이로 띄울 수 있는 코드이다.

``` lisp
(progn
  ;; `overlay'
  ;; ref: https://www.reddit.com/r/emacs/comments/bi4xk1/evaluation_overlays_in_slime_for_common_lisp/
  (require 'cl-lib)
  (require 'eros)
  (defun custom:slime-eval-last-expression-eros ()
    (interactive)
    (let* ((region (slime-region-for-defun-at-point))
           (form (apply #'buffer-substring-no-properties region))
           (pos-end (list (- (cadr region) 1)))
           (expr (slime-eval `(swank:eval-and-grab-output ,form))))
      (cl-destructuring-bind (output value) expr
        (let ((val (concat output value)))
          (eros--make-result-overlay value
            :where pos-end
            :duration eros-eval-result-duration)
          (message value)))))
  ;; (keymap-set slime-mode-map "C-M-x" 'slime-eval-defun)
  (keymap-set slime-mode-map "C-M-x" 'custom:slime-eval-last-expression-eros))

```