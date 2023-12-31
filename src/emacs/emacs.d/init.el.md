# init.el

- `~/.emacs.d/init.el`에는 다음과 같은 일을 할 것입니다.
  - 초기 파일/폴더 관련 설정
  - `package.el`와 `use-package`를 이용해 패키지를 받을 저장소를 지정합니다.

## 초기 파일/폴더 관련 설정

| elisp                  | 설명                                        |
| ---------------------- | ------------------------------------------- |
| custom-file            | 설정파일 경로                               |
| user-emacs-directory   | 초기화 파일이 있는 폴더                     |
| locate-user-emacs-file | `user-emacs-directory`기준 새로운 경로 반환 |
| load                   | 파일을 로드합니다.                          |
| make-backup-files      | 백업파일을 만듭니다.                        |
| create-lockfiles       | lock파일을 만듭니다.                        |

- `~.emacs.d/custom.el`과 같이 하드코딩하는 것은 좋지 않습니다(--init-directory 옵션을 사용할 경우를 대비).
- locate-user-emacs-file 함수를 이용하면 `user-emacs-directory`기준으로 경로를 반환합니다.

``` lisp
(progn ;; `initial-file&directory'
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Saving-Customizations.html
  (setq custom-file (locate-user-emacs-file "custom.el"))
  (load custom-file 'noerror)
  ;; lock 파일 .#파일명
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Backup.html
  (setq make-backup-files nil)
  ;; backup 파일 파일명~
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/elisp/File-Locks.html
  (setq create-lockfiles nil)
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Auto-Save-Control.html
  (setq auto-save-default nil))
```

## package

- [Package Manager](packagemanager.md) 참고
  - package.el: Emacs 24.1(2012-06-10)
  - use-package: Emacs 29.1(2023-07-30)
- Package Archive
  - elpa(`E`macs `L`isp `P`ackage `A`rchive)
  - melpa(`M`ilkypostman `E`macs `L`isp `P`ackage `A`rchive)
- 미러
  - [미러: 칸트대학](https://www.mirrorservice.org/)
  - [미러: 칭화대학](https://mirrors.tuna.tsinghua.edu.cn/help/elpa/)

``` lisp
(use-package package
  ;; 
  ;; ref: https://github.com/emacs-mirror/emacs/blob/master/lisp/emacs-lisp/package.el
  ;; ref: https://www.gnu.org/software/emacs/manual/html_node/emacs/Packages.html
  ;; 
  ;; elpa(`E`macs `L`isp `P`ackage `A`rchive)
  ;; melpa(`M`ilkypostman `E`macs `L`isp `P`ackage `A`rchive)
  ;; 
  ;; elpa(gnu): https://elpa.gnu.org/
  ;; elpa(nognu): https://elpa.nongnu.org/
  ;; melpa: http://melpa.org/
  ;; melpa(stable): http://stable.melpa.org/
  ;; 미러 칸트대학: https://www.mirrorservice.org/
  ;; 미러 칭화대학: https://mirrors.tuna.tsinghua.edu.cn/help/elpa/
  :config
  (progn ;; `elpa'
    (defconst PACKAGE_ELPA_GNU
      '("gnu" . "https://elpa.gnu.org/packages/"))
    (defconst PACKAGE_ELPA_NOGNU
      '("nongnu" . "https://elpa.nongnu.org/nongnu/")))
  (progn ;; `melpa'
    (defconst PACKAGE_MELPA
      '("melpa" . "http://melpa.org/packages/"))
    (defconst PACKAGE_MELPA_STABLE
      '("melpa-stable" . "http://stable.melpa.org/packages/")))
  (progn ;; `mirrorservice'
    (defconst PACKAGE_MIRRORSERVICE_MELPA
      '("melpa" . "http://www.mirrorservice.org/sites/melpa.org/packages/"))
    (defconst PACKAGE_MIRRORSERVICE_MELPA_STABLE
      '("melpa-stable" . "http://www.mirrorservice.org/sites/stable.melpa.org/packages/")))
  (progn ;; `tsinghua'
    (defconst PACKAGE_TSINGHUA_GNU
      '("gnu" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/gnu/"))
    (defconst PACKAGE_TSINGHUA_NOGNU
      '("nognu" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/nongnu/"))
    (defconst PACKAGE_TSINGHUA_MELPA
      '("melpa-cn" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/melpa/"))
    (defconst PACKAGE_TSINGHUA_MELPA_STABLE
      '("melpa-stable-cn" . "http://mirrors.tuna.tsinghua.edu.cn/elpa/stable-melpa/")))

  ;;(setq-default package-user-dir DIR_ROOT_PACKAGE)
  (setq package-archives
    (list
         PACKAGE_ELPA_GNU
         PACKAGE_ELPA_NOGNU
         PACKAGE_MELPA
         )))
```

## config-loader

``` lisp
(progn ;; `설정'
  (thread-last
    "config-loader.el"
    (locate-user-emacs-file)
    (file-truename)
    (load-file))
  (defconst CONFIG_DIR "config/")
  (defconst CONFIG_LIST
    '(
;;; =========== `base-'
      base-define.el
      base-setting.el
;;; =========== `os-'
      os-windows.el
      os-macos.el
      os-linux.el
;;; =========== `setting-'
      setting-theme.el
      setting-ui.el
      setting-navigation.el
      setting-editting.el
      setting-font.el
      setting-treemacs.el
      setting-projectile.el
;;; =========== `lang-' : language(programming)
      lang-emacs-lisp.el
      ;; lang-common-lisp-sly.el
      lang-common-lisp-slime.el
      lang-clojure-cider.el
      lang-racket-racket-mode.el
;;; =========== `file-' : file type
      file-markdown.el
      file-json.el
;;; =========== `util-'
      util-git.el
      util-flymake.el
      util-quickrun.el
      util-command.el
      ;; util-completion.el
      ))
  (config-loader:load-config CONFIG_DIR CONFIG_LIST))
```

## ref

- [emacs-jp/init-loader](https://github.com/emacs-jp/init-loader/)