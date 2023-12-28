# setting-treemacs.el

M-x treemacs를 실행하면 파일트리를 볼 수 있습니다.

``` lisp
;; file: setting-treemacs.el

(use-package treemacs
  ;; ref: https://github.com/Alexander-Miller/treemacs
  :ensure t
  :defer t
  :bind ("<f2>" . treemacs-rename-file)
  :config
  (treemacs-follow-mode +1)
  (treemacs-filewatch-mode +1)
  (treemacs-hide-gitignored-files-mode +1)
  ;; (add-hook 'after-init-hook #'treemacs)
  )

(use-package treemacs-projectile
  :ensure t
  :after (treemacs projectile))

(use-package treemacs-magit
  :ensure t
  :requires (magit)
  :after (treemacs magit))

;; (use-package treemacs-icons-dired
;;   :hook (dired-mode . treemacs-icons-dired-enable-once)
;;   :ensure t)
;; (use-package lsp-treemacs
;;   :ensure t
;;   :after (treemacs)
;;   :config
;;   (add-hook 'prog-mode-hook #'lsp-treemacs-sync-mode))
```