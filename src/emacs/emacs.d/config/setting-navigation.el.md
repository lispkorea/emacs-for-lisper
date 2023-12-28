# setting-navigation.el

이동, 탐색, 버퍼관리 등을 설정한다.

``` lisp
;; file: setting-navigation.el

(progn
  ;; `스크롤'
  (setq redisplay-dont-pause t)
  (setq scroll-margin 1)
  (setq scroll-step 1)
  (setq scroll-conservatively 10000)
  (setq scroll-preserve-screen-position 1)
  ;; `마우스'
  (setq mouse-wheel-follow-mouse 't)
  (setq mouse-wheel-scroll-amount '(1 ((shift) . 1))))

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


(use-package ido-vertical-mode
  ;; ref: https://github.com/creichert/ido-vertical-mode.el
  :ensure t
  :config
  (ido-mode +1)
  (ido-vertical-mode +1)
  (setq ido-vertical-define-keys 'C-n-and-C-p-only))

(use-package amx
  ;; smex => amx
  ;; ref: https://github.com/DarwinAwardWinner/amx
  :ensure t
  :config
  (amx-mode))

```