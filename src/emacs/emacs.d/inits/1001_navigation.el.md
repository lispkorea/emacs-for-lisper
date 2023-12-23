# 1001_navigation.el

``` lisp
;; file: 1001_navigation.el

(use-package projectile
  ;; ref: https://github.com/bbatsov/projectile
  ;; ref: https://docs.projectile.mx/
  :ensure t
  :config
  (setq projectile-enable-caching t)
  (setq projectile-indexing-method 'alien)
  (projectile-mode +1))


(progn ;; `treemacs'
  (use-package treemacs
    ;; ref: https://github.com/Alexander-Miller/treemacs
    :ensure t
    :defer t
    :config
    (treemacs-follow-mode +1)
    (treemacs-filewatch-mode +1)
    (treemacs-hide-gitignored-files-mode +1))
  (use-package treemacs-projectile
    :ensure t
    :after (treemacs projectile)))

(progn ;; `ibuffer'
  (use-package ibuffer
    ;; Emacs(22)
    ;; ref: https://github.com/emacs-mirror/emacs/blob/master/lisp/ibuffer.el
    
    :config
    (defalias 'list-buffers 'ibuffer)
    (setq ibuffer-expert t))
  ;; (use-package nerd-icons-ibuffer
  ;;   ;; ref: https://github.com/seagle0128/nerd-icons-ibuffer
  ;;   :requires ibuffer
  ;;   :ensure t
  ;;   :hook (ibuffer-mode . nerd-icons-ibuffer-mode))
  )
```