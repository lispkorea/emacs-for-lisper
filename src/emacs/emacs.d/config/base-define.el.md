# base-define.el

``` lisp
;; file: 0000_define.el

(defconst true t)
(defconst false nil)

(defconst IS_WINDOWS (eq system-type 'windows-nt))
(defconst IS_MAC (eq system-type 'darwin))

(defconst MODE_ON +1)
(defconst MODE_OFF -1)

(defmacro -> (&rest body)
  (let ((result (pop body)))
    (dolist (form body result)
      (setq result
	    (append (list (car form) result)
                    (cdr form))))))

(defmacro ->> (&rest body)
  (let ((result (pop body)))
    (dolist (form body result)
      (setq result
	    (append form (list result))))))

(defmacro comment (&rest body)
  nil)

(defmacro do (&rest body)
  `(progn
     ,@body))
```