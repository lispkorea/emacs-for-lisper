# inits/0100_lisp-mode.el

- lisp-mode
- imenu
- prettify-symbols-mode

| elisp            | 설명                 |
| ---------------- | -------------------- |
| buffer-file-name | 현재버퍼 파일의 이름 |

``` lisp
(use-package lisp-mode
  :bind
  (("C-c C-l" . (lambda () (interactive) (load-file buffer-file-name)))
   ("C-c C-z" . ielm))
  :config
  (add-hook 'emacs-lisp-mode-hook
	    #'eldoc-mode)
  (add-hook 'emacs-lisp-mode-hook
	    #'(lambda () (imenu-add-to-menubar "@Index")))
  (add-hook 'emacs-lisp-mode-hook
	    #'prettify-symbols-mode)
  (add-hook 'lisp-interaction-mode-hook
	    #'eldoc-mode)
  (add-hook 'eval-expression-minibuffer-setup-hook
	    #'eldoc-mode))
```