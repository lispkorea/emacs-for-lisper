# 모드

## Major 모드 구조

<pre class="mermaid">
---
title: Major 모드 조감도
---

classDiagram
  fundamental-mode <|-- comint-mode
  comint-mode <|-- inferior-emacs-lisp-mode
  note for inferior-emacs-lisp-mode "버퍼: *ielm*"

  fundamental-mode <|-- prog-mode
  prog-mode <|-- lisp-data-mode
  lisp-data-mode <|-- lisp-mode
  lisp-data-mode <|-- emacs-lisp-mode
  emacs-lisp-mode<| -- lisp-interaction-mode 
  note for lisp-interaction-mode "버퍼: *scratch*"

  prog-mode <|-- clojure-ts-mode
  prog-mode <|-- racket-mode
</pre>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
</script>