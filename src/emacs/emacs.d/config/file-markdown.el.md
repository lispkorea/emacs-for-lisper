# file-markdown.el

``` lisp
;; file: file-markdown.el

(use-package markdown-mode
  ;; ref: https://jblevins.org/projects/markdown-mode/
  ;; ref: https://leanpub.com/markdown-mode/
  :ensure t
  :commands (gfm-mode)
  :mode (("\\.md\\'" . markdown-mode)
         ("\\.markdown\\'" . markdown-mode))
  :init (setq markdown-command "multimarkdown"))

(use-package grip-mode
  ;; ref: https://github.com/seagle0128/grip-mode
  ;; ref: grip - https://github.com/joeyespo/grip
  ;; M-x grip-mode
  :ensure t)
```