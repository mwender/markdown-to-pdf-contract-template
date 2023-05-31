# HowTo: Use `md-to-pdf`

Utilize [Markdown to PDF](https://www.npmjs.com/package/md-to-pdf) to generate a PDF from a Markdown file.

## Example

```
$ md-to-pdf markdown-to-pdf.md --stylesheet styles.css --document-title="Example Document Title"
```

The above command will yield `markdown-to-pdf.pdf` with `styles.css` applied and the document title set to "Example Document Title".

## Head Matter

Markdown to PDF supports YAML head matter. Here's the default setup I use:

```
---
pdf_options:
  format: a4
  margin: 30mm 20mm
  printBackground: true
  headerTemplate: |-
    <style>
      section {
        margin: 0 auto;
        font-family: system-ui;
        font-size: 11px;
      }
    </style>
    <section>
      <span class="title"></span>
      <span> &bull; </span>
      <span class="date"></span>
    </section>
  footerTemplate: |-
    <section>
      <div>
        Page <span class="pageNumber"></span>
        of <span class="totalPages"></span>
      </div>
    </section>
---
```

## Markdown to PDF Documentation

  `$ md-to-pdf [options] path/to/file.md`

  Options:

    -h, --help ............... Output usage information
    -v, --version ............ Output version
    -w, --watch .............. Watch the current file(s) for changes
    --watch-options .......... Options for Chokidar's watch call
    --basedir ................ Base directory to be served by the file server
    --stylesheet ............. Path to a local or remote stylesheet (can be passed multiple times)
    --css .................... String of styles
    --document-title ......... Name of the HTML Document.
    --body-class ............. Classes to be added to the body tag (can be passed multiple times)
    --page-media-type ........ Media type to emulate the page with (default: screen)
    --highlight-style ........ Style to be used by highlight.js (default: github)
    --marked-options ......... Set custom options for marked (as a JSON string)
    --pdf-options ............ Set custom options for the generated PDF (as a JSON string)
    --launch-options ......... Set custom launch options for Puppeteer
    --gray-matter-options .... Set custom options for gray-matter
    --port ................... Set the port to run the http server on
    --md-file-encoding ....... Set the file encoding for the markdown file
    --stylesheet-encoding .... Set the file encoding for the stylesheet
    --as-html ................ Output as HTML instead
    --config-file ............ Path to a JSON or JS configuration file
    --devtools ............... Open the browser with devtools instead of creating PDF

  Examples:

  – Convert ./file.md and save to ./file.pdf

    `$ md-to-pdf file.md`

  – Convert all markdown files in current directory

    `$ md-to-pdf ./*.md`

  – Convert all markdown files in current directory recursively

    `$ md-to-pdf ./**/*.md`

  – Convert and enable watch mode

    `$ md-to-pdf ./*.md -w`

  – Convert and enable watch mode with custom options

    `$ md-to-pdf ./*.md --watch --watch-options '{ "atomic": true }'`

  – Convert path/to/file.md with a different base directory

    `$ md-to-pdf path/to/file.md --basedir path`

  – Convert file.md using custom-markdown.css

    `$ md-to-pdf file.md --stylesheet custom-markdown.css`

  – Convert file.md using the Monokai theme for code highlighting

    `$ md-to-pdf file.md --highlight-style monokai`

  – Convert file.md using custom page options

    `$ md-to-pdf file.md --pdf-options '{ "format": "Letter" }'`

  – Convert file.md but save the intermediate HTML instead

    `$ md-to-pdf file.md --as-html`