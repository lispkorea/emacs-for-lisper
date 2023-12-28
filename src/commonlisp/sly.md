# Sly

Sly(`Syl`vester the Cat's Common Lisp IDE)

- [메뉴얼](https://joaotavora.github.io/sly/)
- [저장소](https://github.com/joaotavora/sly)

| 분류 | 단축키  | 내용                   | 함수                          |
| ---- | ------- | ---------------------- | ----------------------------- |
| 평가 |         |                        |                               |
|      | C-M-x   | 현재 폼 평가           | sly-eval-defun                |
|      | C-c C-l | 파일 로드              | sly-load-file                 |
|      | C-c ~   | REPL 네임스페이스 설정 | sly-mrepl-sync                |
| 이동 |         |                        |                               |
|      | M-.     | 정의로 이동            | sly-edit-definition           |
|      | M-,     | 되돌아가기             | sly-pop-find-definition-stack |
|      | C-c C-z | REPL로 이동            | sly-mrepl                     |

## 설정

``` lisp
(use-package sly
  :ensure t
  :init
  (setq inferior-lisp-program (executable-find "sbcl"))
  (define-key sly-mode-map (kbd "C-c M-n") 'sly-mrepl-sync))
```

아래는 `eros`를 이용해서 오버레이로 띄울 수 있는 코드이다.

``` lisp

(progn
  ;; `overlay'
  ;; ref: https://www.reddit.com/r/emacs/comments/bi4xk1/evaluation_overlays_in_slime_for_common_lisp/
  (require 'cl-lib)
  (require 'eros)
  (defun custom:sly-eval-last-expression-eros ()
    (interactive)
    (let* ((region (sly-region-for-defun-at-point))
           (form (apply #'buffer-substring-no-properties region))
           (pos-end (list (- (cadr region) 1)))
           (expr (sly-eval `(slynk:eval-and-grab-output ,form))))
      (cl-destructuring-bind (output value) expr
        (let ((val (concat output value)))
          (eros--make-result-overlay value
            :where pos-end
            :duration eros-eval-result-duration)
          (message value)))))
  ;; (keymap-set sly-mode-map "C-M-x" 'sly-eval-defun)
  (keymap-set sly-mode-map "C-M-x" 'custom:sly-eval-last-expression-eros))
```