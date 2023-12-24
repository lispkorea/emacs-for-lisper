# 패키지 관리자

## 패키지 설정

- package.el Emacs 24.1(2012-06-10)
- use-package: Emacs 29.1(2023-07-30)
- [el-get](https://github.com/dimitri/el-get)
  - Manage the external elisp bits and pieces upon which you depend!
- [leaf.el](https://github.com/conao3/leaf.el)
  - Flexible, declarative, and modern init.el package configuration 
- [straight.el](https://github.com/radian-software/straight.el)
- [elpaca](https://github.com/progfolio/elpaca)
  - Elpaca는 심볼릭 링크가 필수
  - git clone패키지를 설치하고 빌드, + 비동기식으로 처리.


### package.el

- [emacs: package.el](https://github.com/emacs-mirror/emacs/blob/master/lisp/emacs-lisp/package.el)
- [emacs: manual](https://www.gnu.org/software/emacs/manual/html_node/emacs/Packages.html)

| M-x                      |     |
| ------------------------ | --- |
| package-list-packages    |     |
| package-initialize       |     |
| package-refresh-contents |     |
| package-install 패키지명 |     |

### use-package

- [저장소](https://github.com/jwiegley/use-package)
  - [키워드](https://jwiegley.github.io/use-package/keywords/)

|             |                                                                |
| ----------- | -------------------------------------------------------------- |
| :diminish   | diminish.el // 모드 라인 표시 숨기기                           |
| :delight    | delight.el  // 모드 표시 설정                                  |
| :general    | [general.el](https://github.com/noctuid/general.el) // 키 설정 |
| **:ensure** | 패키지를 설치를 보장(t 혹은 다른 패키지 이름)                  |
| **:pin**    | 저장소 키워드(gnu, nognu, elpa ...)                            |

| use-package-keywords        | 설명                                                                   |
| --------------------------- | ---------------------------------------------------------------------- |
| :disabled                   | 로드하지안음                                                           |
| :load-path                  | 해당 위치에서 패키지를 로드                                            |
| :requires                   | 패키지를 로드                                                          |
| :defines                    | 더미 변수 선언(컴파일 워닝방지용)                                      |
| :functions                  | 더미 함수 선언(컴파일 워닝방지용)                                      |
| :preface                    | 조건부 분기 키워드를 동시에 사용하더라도 조건 분기보다 먼저 평가됩니다 |
| :if, :when, :unless         | 조건을 만족시켜야 패키지 로드                                          |
| :no-require                 | ???                                                                    |
| :after                      | 정의된 패키지가 로드 후, 현재 패키지 로드 시작                         |
| :custom                     | 사용자 정의 변수                                                       |
| :custom-face                | 사용자 정의 변수(face)                                                 |
| :bind, :bind*               | 키등록                                                                 |
| :bind-keymap, :bind-keymap* | 키등록(키맵 전용)                                                      |
| :interpreter                | interpreter-mode-alist                                                 |
| :mode                       | auto-mode-alist                                                        |
| :magic, :magic-fallback     | 파일명이 정규표현식에 걸리면 수행                                      |
| :hook                       | add-hook 함수와 같은 기능                                              |
| :commands                   | interactive?                                                           |
| :autoload                   | no-interactive                                                         |
| **:init**                   | 패키지가 **로드되기 전**에 평가됩니다                                  |
| :defer                      |                                                                        |
| :demand                     | ????                                                                   |
| === 패키지 로드 ===         | === 패키지 로드 ===                                                    |
| **:config**                 | 해당 패키지가 **로드된 후**에 평가됩니다                               |


## 설정

- [init-loader](https://github.com/emacs-jp/init-loader)
