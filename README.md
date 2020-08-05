# Book Template

Template for Book.

## How To Generate the Book

You can generate the e-book files manually with Asciidoctor.
If you run the following you will get HTML, Epub and PDF output files:

```bash
bundle install
bundle exec rake book:build
```

Output shall be

```txt
Converting to HTML...
 -- HTML output at ./build/book-template.html
Converting to EPub...
 -- Epub output at ./build/book-template.epub
Converting to PDF... (this one takes a while)
 -- PDF output at ./build/book-template.pdf
```
