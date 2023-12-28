# lang-emacs-lisp.el

- lisp-mode
- imenu
- prettify-symbols-mode

| elisp            | 설명                 |
| ---------------- | -------------------- |
| buffer-file-name | 현재버퍼 파일의 이름 |

``` lisp
(use-package emacs-lisp-mode
  :bind
  (("C-c C-l" . (lambda () (interactive) (load-file buffer-file-name)))
   ("C-c C-z" . ielm))
  :config
  (add-hook 'emacs-lisp-mode-hook
	    #'eldoc-mode)
  ;; ref: imenu - https://www.gnu.org/software/emacs/manual/html_node/emacs/Imenu.html
  (add-hook 'emacs-lisp-mode-hook
	    #'(lambda () (imenu-add-to-menubar "@Index")))
  ;; ref: prettify-symbols-mode - prog-mode.el
  (add-hook 'emacs-lisp-mode-hook
	    #'prettify-symbols-mode)
  ;; ref: inferior-emacs-lisp-mode "버퍼: *ielm*"
  (add-hook 'lisp-interaction-mode-hook
	    #'eldoc-mode)
  (add-hook 'eval-expression-minibuffer-setup-hook
	    #'eldoc-mode))
```
