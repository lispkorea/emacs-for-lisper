# setting-font.el

폰트설정. 고정폭이 제대로 적용(한글과 영어간격)되는지, 폰트가 잘 보이는지 확인한다.

``` lisp
;; file: setting-font.el

;; https://dejavu-fonts.github.io/
;; https://github.com/naver/d2codingfont
;; https://www.google.com/get/noto/help/cjk/
;; ref: https://www.emacswiki.org/emacs/SetFonts

;; 0 o O l L i I 1 !
;; , . "" '' ``
;; ;:|\/
;; [](){}<>
;; +-*~
;; S s C c V v P p

;; 한글 테스트
;; AABB CCDDEE

;; abcdefghijklmnopqrstuvwxyz
;; ABCDEFGHIJKLMNOPQRSTUVWXYZ
;; Ξεσκεπάζω την ψυχοφθόρα βδελυγμία.
;; αβγδεζηθικλμνξοπρστυφχψως
;; ΑΒΓΔΕΖΗΘΙΚΛΜΝΞΟΠΡΣΤΥΦΧΨΩ
;; У рудога вераб’я ў сховішчы
;; пад фатэлем ляжаць нейкія гаючыя зёлкі.
;; абвгґдђѓеёєжнњопрс
;; тћќуўuфхцчџшщъыьэюя
;; АБВГҐДЂЃЕЁЄЖНЊОПРС
;; ТЋЌУЎUФХЦЧЏШЩЪЫЬЭЮЯ
;; & 1234567890 .,:;… ¡!¿?
;; '" ‘’ “” ‚„ ′″‹› «» -–—
;; (/)[|]{\} * †‡§¶|‖ @ №
;; $£¥€₹₺₽¢ƒ %‰ ¼½¾⅓⅔⅛⅜⅝
;; +−×÷∙=<>≤≥±^≠~≈¬ #π∞µ∂∫√
;; •◦▪▫▴▸▾◂▵▹▿◃
;; ●○■□▲▶▼◀△▷▽◁❒◆►◄◙◉◘
;; ←↖↑↗→↘↓↙ ⇐⇑⇒⇓ ↔↕↨ ♀♂ ☼⌂ ☑ ✓
;; ♪ ♫ ♥ ​♣​ ♦​ ♠​ ☺​ ☻ ​❤​ ☕​ 💩 ​🤖​ 🔒
;;      

(when (display-graphic-p)
  ;; `비쥬얼::폰트_all-the-icons'
  ;; ref: https://github.com/domtronn/all-the-icons.el
  (use-package all-the-icons
    :ensure t
    :if (or (display-graphic-p)
            (daemonp))
    :config
    ;; ref: https://github.com/domtronn/all-the-icons.el/issues/120#issuecomment-565438080
    (defun aorst/font-installed-p (font-name)
      "Check if font with FONT-NAME is available."
      (if (find-font (font-spec :name font-name))
          t
        nil))
    (when (and (not (aorst/font-installed-p "all-the-icons"))
               (window-system))
      (all-the-icons-install-fonts t)))
  (use-package all-the-icons-dired
    ;; https://github.com/jtbm37/all-the-icons-dired
    :ensure t
    :after (all-the-icons dired)
    :hook (dired-mode . all-the-icons-dired-mode))
  (use-package all-the-icons-ibuffer
    ;; https://github.com/seagle0128/all-the-icons-ibuffer
    :ensure t
    :after (all-the-icons ibuffer)
    :hook (ibuffer-mode . all-the-icons-ibuffer-mode)))


(when (display-graphic-p)
  (defun available-font? (font)
    (->> (font-family-list)
         (member font)))
  (let ((font-name "D2Coding"))
    (when (available-font? font-name)
      (set-face-font 'default font-name)
      (set-frame-font font-name nil t)
      (set-fontset-font "fontset-default" '(#x1100 . #x11ff) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '#x20a9 (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#x302e . #x302f) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#x3130 . #x318f) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#x3200 . #x321e) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#x3260 . #x327f) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#xa960 . #xa97f) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#xac00 . #xd7a3) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#xd7b0 . #xd7ff) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '(#xffa1 . #xffdc) (cons font-name "iso10646"))
      (set-fontset-font "fontset-default" '#xffe6 (cons font-name "iso10646"))
      (set-fontset-font t 'hangul (font-spec :name font-name))
      (set-face-attribute 'default nil :family font-name)
      (setq face-font-rescale-alist
            '((font-name . 1))))))
```