# setting-editting.el

편집활동에 도움이 되는것들을 설정한다.

``` lisp
;; file: setting-editting.el


(use-package electric-pair-mode
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Matching.html
  :ensure nil
  :init
  (require 'elec-pair)
  (setq electric-pair-preserve-balance t)
  (add-hook 'prog-mode-hook #'electric-pair-local-mode))


(use-package apheleia
  ;; ref: https://github.com/radian-software/apheleia
  ;; Run code formatter on buffer contents without moving point, using RCS patches and dynamic programming
  :ensure t
  :demand
  :config
  (add-hook 'clojure-mode-hook #'apheleia-mode)
  (add-hook 'emacs-lisp-mode-hook #'apheleia-mode)

  (setf (alist-get 'cljstyle     apheleia-formatters) '("cljstyle" "pipe"))
  (setf (alist-get 'clojure-mode apheleia-mode-alist) 'cljstyle)
  )


(use-package multiple-cursors
  ;; ref: https://github.com/magnars/multiple-cursors.el
  :ensure t
  :bind
  (("C-M-<return>" . mc/mark-more-like-this-extended)))

(use-package move-text
  ;; ref: https://github.com/emacsfodder/move-text
  :ensure t
  :bind
  (("M-<up>" . move-text-up)
   ("M-<down>" . move-text-down)))
```