# dummy_quarto_listing
A basic project to test quarto's listing

# Problem

Rendering a single markdown file to html and pdf with a listing in `index.qmd` will corrupt the pdf output.

# Environment setup

- Problem occuring on Windows 10
- Quarto v1.3.450 installed from the official website https://quarto.org/docs/get-started/ 
- TinyTex installed with `quarto install tinytex`
- Command lines executed from a GitBash command prompt

# Steps to reproduce

## First build

1. Clone the project
1. Run `quarto render doc/file.qmd`
    * `doc/file.html` is generated successfully
    * `doc/file.pdf` is generated successfully
    * `doc/other_file.qmd` is not compiled
    * a default `index.html` is generated but it simply points to `doc/file.html`

Everything is working well

## Second build

1. Run `quarto render`
    * `doc/file.html` is generated successfully
    * `doc/file.pdf` is generated successfully
    * `doc/other_file.html` is generated successfully
    * `doc/other_file.pdf` is generated successfully
    * `index.html` is generated, containing the content of `index.qmd`

Everything is working well

## Third build

1. Run `quarto render doc/file.qmd`
    * `doc/file.html` is generated successfully
    * `doc/file.pdf` is generated but corrupted (can't open it)
    * `doc/other_file.qmd` is not compiled
    * `index.qmd` is compiled again and `index.html` is generated successfully

Problem: the `doc/file.pdf` is corrupted

## Fourth build

1. Remove the `listing` parameter from the `index.qmd` yaml block
1. Run `quarto render`
    * all files are compiled successfully
1. Run `quarto render doc/file.qmd`
    * `doc/file.html` is generated successfully
    * `doc/file.pdf` is generated successfully
    * `doc/other_file.qmd` is not compiled
    * `index.qmd` is not compiled

Everything is working well again