# Cider

CIDER(`C`lojure(Script) `I`nteractive `D`evelopment `E`nvironment that `R`ocks!)

- [저장소](https://github.com/clojure-emacs/cider)
- [문서](https://docs.cider.mx/cider/index.html)

## 단축키

| 분류       | 단축키          | 내용                    | 함수                          |
| ---------- | --------------- | ----------------------- | ----------------------------- |
| 평가       |                 |                         |                               |
|            | C-M-x           | 현재 폼을 평가합니다    | cider-eval-defun-at-point     |
|            | C-c M-;         |                         | cider-eval-defun-to-comment   |
|            | C-c C-e         |                         | cider-eval-last-sexp          |
|            | C-c C-m         | 매크로 확장(1단계)      | cider-macroexpand-1           |
|            | C-c M-m         | 매크로 확장(전체)       | cider-macroexpand-all         |
|            | C-c M-n (M-)n   | REPL 네임스페이스 설정  | cider-repl-set-ns             |
| 이동       |                 |                         |                               |
|            | M-.             | 정의로 이동             | cider-find-var                |
|            | M-,             | 되돌아가기              | cider-pop-back                |
|            | C-c C-z         | REPL로 이동             | cider-switch-to-repl-buffer   |
| 헬퍼       |                 |                         |                               |
|            | M-TAB           | 자동완성                | complete-symbol               |
| 문서       |                 |                         |                               |
|            | C-c C-d C-d     | 문서보기(클로저)        | cider-doc                     |
|            | C-c C-d C-j     | 문서보기(자바)          | cider-javadoc                 |
| 접속관련   |                 |                         |                               |
|            | C-c C-x C-c C-j | 접속                    | cider-connect-clj             |
|            | C-c C-q         | 종료                    | cider-quit                    |
|            | C-c M-r         | 재시작                  | cider-restart                 |
| 테스트     |                 |                         |                               |
|            | C-c C-t C-t     | 테스트                  | cider-test-run-test           |
|            | C-c C-t C-g     | 테스트(다시)            | cider-test-rerun-test         |
|            | C-c C-t C-n     | 테스트(현재 이름공간만) | cider-test-run-ns-tests       |
|            | C-c C-t C-r     | 테스트(실패한 테스트만) | cider-test-rerun-failed-tests |
| 멈추었을시 |                 |                         |                               |
|            | C-c C-b         | 인터럽트 시그날         | cider-interrupt               |
