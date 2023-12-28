# setting-editting.el

``` lisp
;; file: 1002_editting.el

(use-package smartparens-mode
  :ensure smartparens			    ;; install the package
  :hook (prog-mode text-mode markdown-mode) ;; add `smartparens-mode` to these hooks
  :config
  ;; load default config
  (require 'smartparens-config))
```