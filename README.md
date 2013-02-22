SCIENCE
=======

1. Install Pandoc - http://johnmacfarlane.net/pandoc/index.html
2. Branchin model - http://tinyurl.com/39hd87l
3. Push Markdown source only! - http://daringfireball.net/projects/markdown/syntax
                              - It can be pandoc Markdown (supports LaTeX math syntax) http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown
4.  To prevent messy merges, before you start a topic, put a placeholder with
    your name on it in the document - goes without saying to also check that
    your topic isn't currently being authored by someone else.

Compiling to HTML
-----------------

Currently I (Softly) use the following to compile from markdown to HTML:

`pandoc --smart --standalone --table-of-contents --mathml --from=markdown --to=html input.md --output=output.html`
