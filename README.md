# IncludeSupplement

A method for including supplemental materials files on the arXiv.

This repository includes information on how to include a supplemental materials file as a separate PDF file when co-submitting a paper to the arXiv as well as journals.  It uses the `pdfpages` and `pgffor` latex packages.  To proceed:

## Instructions 
1. Generate `supplement.pdf` by running latex/bibtex to create a stand-alone PDF file
2. Run latex/bibtex on `manuscript.tex` to produce the combined `manuscript.pdf` file.
