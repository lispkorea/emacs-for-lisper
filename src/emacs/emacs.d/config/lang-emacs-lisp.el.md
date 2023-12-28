# lang-emacs-lisp.el

- lisp-mode
- imenu
- prettify-symbols-mode

| elisp            | 설명                 |
| ---------------- | -------------------- |
| buffer-file-name | 현재버퍼 파일의 이름 |

``` lisp
;; file: lang-emacs-lisp.el

(use-package emacs-lisp-mode
  :ensure nil
  :bind
  (("C-c C-l" . (lambda () (interactive) (load-file buffer-file-name)))
   ("C-c C-z" . ielm))
  :init
  (add-hook 'emacs-lisp-mode-hook
            #'eldoc-mode)
  ;; ref: imenu - https://www.gnu.org/software/emacs/manual/html_node/emacs/Imenu.html
  (add-hook 'emacs-lisp-mode-hook
            #'(lambda () (imenu-add-to-menubar "@Index")))
  ;; ref: prettify-symbols-mode - prog-mode.el
  (add-hook 'emacs-lisp-mode-hook
            #'prettify-symbols-mode)
  ;; ref: https://stackoverflow.com/a/6914626
  ;; (add-hook 'emacs-lisp-mode-hook
  ;;           '(lambda ()
  ;;              (set (make-local-variable lisp-indent-function)
  ;;                   'common-lisp-indent-function)))
  ;; ref: inferior-emacs-lisp-mode "버퍼: *ielm*"
  (add-hook 'lisp-interaction-mode-hook
            #'eldoc-mode)
  (add-hook 'eval-expression-minibuffer-setup-hook
            #'eldoc-mode))

(use-package eldoc
  :ensure nil
  :diminish eldoc-mode
  :config
  (setq eldoc-idle-delay 0.4))

;; (use-package eldoc-box
;;   :ensure t
;;   :config
;;   (add-hook 'emacs-lisp-mode-hook #'eldoc-box-hover-at-point-mode))

(use-package eros
  ;; eros(Evaluation Result OverlayS for Emacs Lisp)
  ;; ref: https://github.com/xiongtx/eros
  :ensure t
  :config
  (add-hook 'emacs-lisp-mode-hook
            #'eros-mode))

(use-package elisp-autofmt
  ;; ref: https://codeberg.org/ideasman42/emacs-elisp-autofmt
  :ensure t)


(use-package highlight-defined
  ;; ref: https://github.com/Fanael/highlight-defined
  :ensure t
  :config
  (add-hook 'emacs-lisp-mode-hook
            #'highlight-defined-mode))

(use-package aggressive-indent
  ;; ref: https://github.com/Malabarba/aggressive-indent-mode
  :ensure t
  :config
  (add-hook 'emacs-lisp-mode-hook
            #'aggressive-indent-mode))


(use-package keycast
  ;; ref: https://github.com/tarsius/keycast
  ;; 모드라인: keycast-mode-line-mode
  ;; 헤드라인: keycast-header-line-mode
  ;; 탭 바: keycast-tab-bar-mode
  ;; 다른 프레임: keycast-log-mode
  :ensure t)

```
