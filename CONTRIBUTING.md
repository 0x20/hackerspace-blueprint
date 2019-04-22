# Contributing to the hackerspace blueprint

## Building the book

First install the build tools.

```bash
sudo apt install pandoc texlive-plain-generic texlive-latex-extra texlive-fonts-recommended texlive-fonts-extra texlive-extra-utils
```

Generate the print version using `pandoc`.

```bash
  # Generate epub
  pandoc --verbose pandoc-metadata.yaml README.md [0-9]*.md -o hackerspace-blueprint.epub --metadata date="`date +%D`" --toc-depth=2 --epub-embed-font='epub-fonts/*.ttf' --css=epub.css
  # Generate PDF
  pandoc --verbose pandoc-metadata.yaml README.md [0-9]*.md -o hackerspace-blueprint.pdf --metadata date="`date +%D`" --template eisvogel.tex --include-before-body=include-cover.tex --include-after-body=include-back.tex
  # Generate booklet
  numpages=$(pdfinfo hackerspace-blueprint.pdf | awk '/^Pages/ { print $2}')
  pdfbook hackerspace-blueprint.pdf 2-$(($numpages-2)) -o hackerspace-blueprint-booklet-body.pdf
```
