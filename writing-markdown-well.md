Writing markdown well
=====================

*Note: work in progress, heavily...*

Most important messages.
Explain all.
Add relevant examples of alternative ways,
and explain why they are inferior.
Add examples of common mistakes.

- headings
  - use `====`, `----` and `###` for headings
  - use `====` style instead of `#`
  - use `----` style instead of `#`
  - don't use lower level than `###`
  - pay attention to semantics

- inline // -> move to concept category, "inline" not interesting
  - when to use backticks
  - when to use `*`
  - when to use `**`

- simplicity
  - don't use deeply nested, tricky structures
  - don't use html
  - don't use `&amp;` etc
  - don't use line breaks (two space at end of line)

- readability
  - horizontal spacing
    + space before starting `*` and after closing `*`
  - vertical spacing
    + empty line between heading and body
    + empty line between paragraph and list
    + empty line around horizontal rule
  - prefer `====` and `----` for headings
  - prefer indented code blocks over fenced code blocks
  - number properly in numbered lists
  - break lines between list items if too long
  - align list items
  - use different symbol at different levels // matter of taste
  - use horizontal rules in consistent format
  - prefer `*` over `_`
  - don't use `_` for horizontal rule

- compatibility
  - prefer indented code blocks over fenced code blocks
  - don't use below `###`

- links
  - prefer `[title][name]` + reference over inline `[title](link)`

- summary of recommendations against daring fireball
  - don't use HTML
  - don't bother escaping HTML entities such as `&amp;` etc
  - don't use line breaks (two space at end of line)
  - don't use below `###`
  - don't use fenced code blocks
  - number properly in numbered lists
  - don't be lazy
  - don't put code blocks inside lists
  - indent with 4 spaces instead of tabs

- publisher rules
  - paragraph between heading and sub-heading or list
  - `*` for keywords, key terms, on first occurrence only

- semantics
  - use headings right
  - forget italic and bold, think emphasis and important
  - use `*` and `**` and backticks right

- lazyness
  - don't bother closing `###` headers
  - `---` seems perfectly reasonable for horizontal rules
  - `-` easiest to write as bullet

Philosophy
----------

Markdown is meant to make plain-text documents structured and look good.
Easy to read, easy to write, simple, even without fancy rendering.

Guiding principles:

- Redability
- Semanting correctness
- Simplicity
- Compatibility

TODO: maybe instead of the following intro sub-sections,
just go ahead with the final text.

### Readability

5 equivalent ways of writing a document title:

    Document    Document    Document    # Document  #Document
    =           ===         ========

Which is the most readable?

---

Valid markdown examples, but which one is easier to read?

    -Requirements
    -Building
    -Running

### Semantic correctness

TODO

### Simplicity

TODO

### Compatibility

TODO

Headings
--------

Headings drive the structure of a document,
it's important that they are loud and clear.

Underline the document title using `=`,
as many `=` as letters in the title.
This corresponds to H1 headings in HTML.
There should be only one such heading in a document.

Prefixing the title with `#` has the same effect when rendered,
but doesn't stand out enough in plain text.

Underline section headings using `-`,
using as many `-` as letters in the heading.
This corresponds to H2 headings in HTML.

Prefixing the title with `##` has the same effect when rendered,
but doesn't stand out enough in plain text.


Inline rules
------------

Inline formats and when to use them:

- `inline code`: use backticks for code-like things, such as:
  + class names
  + function names
  + variable names
  + very short inline example code
  + program names
  + filenames

- *emphasis*: use single asterisks for emphasis, such as:
  + keywords of your system, when defined for the first time
  + key terms, for example *single responsibility principle*

- **strong emphasis**: use double asterisks for strong emphasis
  + window names
  + menu item names

Combine elements as necessary,
for example to link to the JavaDoc of [`Comparable`][comparable]

Links
-----

http://commonmark.org/

http://blog.codinghorror.com/standard-flavored-markdown/

[syntax]: https://daringfireball.net/projects/markdown/syntax
[comparable]: https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html
