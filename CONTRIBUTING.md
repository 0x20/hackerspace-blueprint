# Contributing to Hack the Hackerspace

## Building Hack the Hackerspace

First install the build tools.

```bash
sudo apt install pandoc
```

Generate the print version using `pandoc`.

```bash
pandoc --toc -V links-as-notes README.md [0-9]*.md -o hack-the-hackerspace.pdf
```
