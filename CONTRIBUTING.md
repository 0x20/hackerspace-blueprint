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
