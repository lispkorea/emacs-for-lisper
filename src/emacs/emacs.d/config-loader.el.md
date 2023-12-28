# config-loader.el

리스트에 나열된 설정파일들을 로드하고, 로드된 결과를 보여줍니다.

``` lisp
;; file: config-loader.el

(require 'cl-lib)
(require 'cl-seq)

(defalias '-> 'thread-first)
(defalias '->> 'thread-last)

(cl-defstruct ConfigInfo
  index
  file-path
  file-fullpath
  time-load-sec)

(defun getConfigInfos (config-dir config-list)
  (cl-loop for file-path in config-list
           for index from 0
           for file-fullpath = (->> file-path
                                    (symbol-name)
                                    (concat config-dir)
                                    (locate-user-emacs-file)
                                    (file-truename))
           when (file-exists-p file-fullpath)
           collect
           (let* ((time-load-sec (-> file-fullpath
                                     (load-file)
                                     (benchmark-run)
                                     (car))))
             (make-ConfigInfo :index (+ index 1)
                              :file-path file-path
                              :file-fullpath file-fullpath
                              :time-load-sec time-load-sec))))

(defun getIndicate (val-cur val-max)
  (let* ((perc-1 (thread-first
                   val-cur
                   (/ val-max)
                   (* 10)
                   (round)))
         (perc-2 (- 10 perc-1)))
    (concat (make-string perc-1 ?■) (make-string perc-2 ?.))))

(defun config-loader:load-config (config-dir config-list)
  (let* ((infos (getConfigInfos config-dir config-list))
         (acc-sec (->> infos
                       (mapcar #'ConfigInfo-time-load-sec)
                       (apply '+ ))))
    (let ((buff (get-buffer-create "== 설정 로드 결과 ==")))
      (with-current-buffer buff
        (view-mode -1)
        (erase-buffer)
        (insert (format "\n\n총 %d파일, %0.4f초\n\n" (length infos) acc-sec))
        (dolist (info infos)
          (insert (format "%03d | %s | %0.2f초 | %s\n"
                          (ConfigInfo-index info)
                          (getIndicate (ConfigInfo-time-load-sec info) acc-sec)
                          (ConfigInfo-time-load-sec info)
                          (ConfigInfo-file-path info))))
        (switch-to-buffer buff)
        (view-mode +1)))))
```