# 기본 조작법

**`Ctrl-G`** 중요합니다.

| 키         | 기호 |
| ---------- | ---- |
| Ctrl       | C    |
| Alt/Option | M    |
| Shift      | S    |

## 필수 조작법

| 필수        | 단축키     |
| ----------- | ---------- |
| **중단**    | `C-g`      |
| 파일 열기   | C-x C-f    |
| 저장하기    | C-x C-s    |
| 종료        | C-x C-c    |
| 명령어 실행 | M-x 명령어 |


## 이동

| C-이동                 | 단축키 | M-이동           | 단축키       |
| ---------------------- | ------ | ---------------- | ------------ |
| 문자 앞(forward)       | C-f    | 단어 앞(forward) | M-f          |
| 문자 뒤(back)          | C-b    | 단어 뒤(back)    | M-b          |
| 라인 위(previous-line) | C-p    |                  |              |
| 라인 아래(next-line)   | C-n    |                  |              |
| 라인 앞                | C-a    | 문단 앞          | M-a          |
| 라인 뒤                | C-e    | 문단 뒤          | M-e          |
|                        |        | 라인으로 이동    | M-g M-g 라인 |

[![emacs-movement.png](../res/emacs-movement.png)](../res/emacs-movement.png)
- [출처](https://punchcard.wordpress.com/2010/10/09/emacs-movement-shortcuts-wallpaper/)

## 튜토리얼 시작

위에 필수과 이동을 잘 숙지 후,  `M-x help-with-tutorial-spec-language`후 `Korean`을 입력하시면 한글로 튜토리얼을 볼 수 있습니다.

## 기타

### 삭제

| 이동             | 단축키                         | 이동             | 단축키    |
| ---------------- | ------------------------------ | ---------------- | --------- |
| C-k              | 현재 커서에서 라인 끝까지 삭제 | M-k              | 버퍼 삭제 |
| 이전 문자 지우기 | `<Del>`                        | 이전 단어 지우기 | M-`<Del>` |
| 다음 문자 지우기 | C-d                            | 다음 단어 지우기 | M-d       |

### 복사, 붙여넣기, 되돌리기

| 복사, 붙여넣기, 되돌리기 | 단축키    |
| ------------------------ | --------- |
| 마크 설정                | C-`<SPC>` |
| 마크 전체                | C-x h     |
| 마크된 영역 `복사`       | M-w       |
| 마크된 영역 `잘라내기`   | C-w       |
| `붙여넣기`               | C-y       |
| `되돌리기`               | C-x u     |
| `되돌리기`               | C-/       |

### 확대축소

| 확대축소              | 단축키    |                       |
| --------------------- | --------- | --------------------- |
| 확대                  | C-x C-`-` |                       |
| 축소                  | C-x C-`=` |                       |
| 자동줄바꿈(껏다 켰다) | C-x x t   | toggle-truncate-lines |

### 검색

| 검색               | 단축키 |
| ------------------ | ------ |
| 정방향             | C-s    |
| 역방향             | C-r    |
| 정방향(정규표현식) | C-M-s  |
| 역방향(정규표현식) | C-M-r  |
| 바꾸기             | M-%    |
| 바꾸기(정규표현식) | C-M-%  |


## shell

- <https://unix.stackexchange.com/a/180129>
  - M-x shell
    - {grep, du, ls, sort, cat, head, tail, uname, ...}와 같은 클래식/표준 Unix 쉘 명령의 일반적인 사용에 적합합니다.
  - M-x term ＆ M-x ansi-term
    - ssh나 기타 명령줄 대화형 인터페이스(예: {python, ruby, lisp} 셸) 또는 {vim, synaptic, …}과 같은 텍스트 기반 GUI 앱을 실행하려는 경우에 좋습니다.
  - M-x eshell
    - eshell은 emacs lisp에 직접 액세스할 수 있기 때문에 bash가 설치되지 않은 Microsoft Windows에서 특히 좋습니다. 또는 emacs lisp 프로그래머라면 더욱 좋습니다.

## 버퍼, 윈도우, 프레임, 탭

**버퍼**와 **윈도우**를 자주 사용합니다.

### 버퍼

| **버퍼**       | 단축키  |
| -------------- | ------- |
| 목록           | C-x C-b |
| 이동           | C-x b   |
| 삭제           | C-x k   |
| 읽기전용(토클) | C-x C-q |

### 윈도우

|                     | **윈도우** | 프레임    | 탭        |
| ------------------- | ---------- | --------- | --------- |
| 현재창 닫기         | C-x 0      | C-x 5 0   | C-x t 0   |
| 다른창 닫기         | C-x 1      | C-x 5 1   | C-x t 1   |
| 새로만들기          | C-x 2      | C-x 5 2   | C-x t 2   |
| 새로만들기(우측)    | C-x 3      |           |           |
| 다음으로 이동       | C-x o      | C-x 5 o   | C-x t o   |
| 파일 열기           | C-x C-f    | C-x 5 C-f | C-x t C-f |
| 파일 열기(읽기전용) | C-x C-r    | C-x 5 r   | C-x t C-r |


## 참고

- [TUTORIAL.ko](https://github.com/emacs-mirror/emacs/blob/master/etc/tutorials/TUTORIAL.ko)
- [emacs: wiki](https://www.emacswiki.org/)
- [emacs(영문): 메뉴얼](https://www.gnu.org/software/emacs/manual/)
- [emacs(영문): 투어](https://www.gnu.org/software/emacs/tour/)
