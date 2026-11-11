---
name: feedback_math_in_kable_tables
description: How to reliably render LaTeX math in kableExtra tables in Quarto revealjs slides
metadata:
  type: feedback
---

For Quarto revealjs slides, use `\(...\)` delimiters (written as `"\\(...\\)"` in R strings) instead of `$...$` for math in kableExtra tables. MathJax v3's reveal.js plugin treats `\(...\)` as its native inline delimiter and reliably processes it in R-generated HTML (`<th>` headers and `<td>` cells), whereas `$...$` is inconsistently picked up.

**Why:** `$...$` in R chunk HTML output is not reliably scanned by the reveal.js math plugin; `\(...\)` is MathJax v3's canonical delimiter and always works.

**How to apply:** When building kable tables with math column names or math cell values, write delimiters as `"\\(Y_i^*\\)"` in col.names and cell value strings, with `escape = FALSE` in `kable()`.
