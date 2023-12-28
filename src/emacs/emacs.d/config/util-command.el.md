# util-command.el

``` lisp
;; file: util-command.el

(use-package urgrep
  ;; ref: https://github.com/jimporter/urgrep
  :ensure t)

(use-package ag
  :ensure t
  :commands (ag)
  :config
  (setq ag-highlight-search t)
  (setq ag-group-matches nil))
```
