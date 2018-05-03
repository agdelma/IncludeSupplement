# IncludeSupplement

A simple method for including supplemental materials files on the arXiv.

This repository includes information on how to include a supplemental materials file as a stand-alone PDF file when co-submitting a paper to the arXiv and a journal.  It uses the `pdfpages` and `pgffor` latex packages.  

## Usage 
1. Generate `supplement.pdf` by running `pdflatex/bibtex` on `supplement.tex` to create a stand-alone PDF file
2. Run `pdflatex/bibtex` on `manuscript.tex` to produce the combined `manuscript.pdf` file.
3. Upload `manuscript.tex`, `manuscript.bbl` and `supplement.pdf` to the arXiv.
