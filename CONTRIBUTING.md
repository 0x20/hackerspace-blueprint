# Contributing to Hack the Hackerspace

## Building Hack the Hackerspace

First install the build tools.

```bash
sudo apt install pandoc texlive-plain-generic texlive-latex-extra texlive-fonts-recommended texlive-fonts-extra
```

Generate the print version using `pandoc`.

```bash
pandoc pandoc-metadata.yaml README.md [0-9]*.md -o hack-the-hackerspace.pdf --template eisvogel.tex --toc --listings --metadata date="`date +%D`" --include-before-body=include-cover.tex
```

Generate the booklet version from the print version. The cover and back should be printed separately.

```bash
pandoc --verbose pandoc-metadata.yaml README.md [0-9]*.md -o hack-the-hackerspace.pdf --template eisvogel.tex --toc --listings --metadata date="`date +%D`" --include-before-body=include-cover.tex
numpages=$(pdfinfo hack-the-hackerspace.pdf | awk '/^Pages/ { print $2}')
pdfbook hack-the-hackerspace.pdf 2-$(($numpages-2)) -o hack-the-hackerspace-booklet-body.pdf
```
