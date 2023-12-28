# base-define.el

``` lisp
;; file: base-define.el

(defconst true t)
(defconst false nil)

(defconst IS_WINDOWS (eq system-type 'windows-nt))
(defconst IS_MAC (eq system-type 'darwin))
(defconst IS_LINUX (eq system-type 'gnu/linux))

(defconst MODE_ON +1)
(defconst MODE_OFF -1)

;; (defmacro -> (&rest body)
;;   ;; thread-first
;;   (let ((result (pop body)))
;;     (dolist (form body result)
;;       (setq result
;;             (append (list (car form) result)
;;                     (cdr form))))))
;; (defmacro ->> (&rest body)
;;   ;; thread-last
;;   (let ((result (pop body)))
;;     (dolist (form body result)
;;       (setq result
;;             (append form (list result))))))

(defmacro comment (&rest body)
  nil)

(defalias 'count 'length)
(defalias 'first 'car)
(defalias 'rest 'cdr)
(defalias 'do 'progn)

(defalias 'provided? 'featurep)
(defalias '-> 'thread-first)
(defalias '->> 'thread-last)
(defun inc (n) (+ 1 n))

```