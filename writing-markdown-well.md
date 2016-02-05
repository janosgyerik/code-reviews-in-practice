Writing markdown well
=====================

*Note: work in progress, heavily...*

Philosophy
----------

Markdown is meant to make plain-text documents structured and look good.
Easy to read, easy to write, simple, even without fancy rendering.

Guiding principles:

- Redability
- Semanting correctness
- Simplicity
- Compatibility

5 equivalent ways of writing a document title:

    Document    Document    Document    # Document  #Document
    =           ===         ========

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
