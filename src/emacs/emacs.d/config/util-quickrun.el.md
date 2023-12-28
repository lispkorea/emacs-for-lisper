# util-quickrun.el

``` lisp
;; file: util-quickrun.el

(use-package quickrun
  :ensure t
  :bind
  (("<f7>" . quickrun)
   ("<f8>" . quickrun-compile-only)))
```