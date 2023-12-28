# 색상 테마

- [emacsthemes](https://emacsthemes.com/popular/index.html)에서 여러가지 테마를 확인 해 볼 수 있습니다.

## 추천

- 모드라인과도 잘 연동이 되는 doom 시리즈를 추천합니다.
  - [doom theme](https://github.com/doomemacs/themes)
  - [doom-modeline](https://github.com/seagle0128/doom-modeline)

``` lisp
(use-package doom-modeline
  ;; ref: https://github.com/seagle0128/doom-modeline
  :ensure t
  :config
  ;; (setq doom-modeline-minor-modes t)
  (setq doom-modeline-project-detection 'projectile)
  (setq doom-modeline-position-column-line-format '("%l"))
  (setq doom-modeline-total-line-number t)
  (setq doom-modeline-height 20)
  (setq doom-modeline-bar-width 5)
  (setq doom-modeline-icon t)
  ;; (setq doom-modeline-buffer-file-name-style 'truncate-upto-project)
  (setq doom-modeline-buffer-file-name-style 'relative-to-project)
  (add-hook 'after-init-hook #'doom-modeline-mode))

(use-package doom-themes
  ;; ref: https://github.com/doomemacs/themes
  ;; themelist: https://github.com/doomemacs/themes#theme-list
  :ensure t
  :config
  (doom-themes-visual-bell-config)
  (load-theme 'doom-tomorrow-day t))
```

## 기타

- [zenburn](https://github.com/bbatsov/zenburn-emacs)
- [solarized](https://github.com/bbatsov/solarized-emacs)
- [tomorrow-night](https://github.com/purcell/color-theme-sanityinc-tomorrow)