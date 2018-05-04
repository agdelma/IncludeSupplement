# IncludeSupplement

A simple method for including supplemental materials files on the arXiv.

This repository includes information on how to include a supplemental materials file as a stand-alone PDF file when co-submitting a paper to the arXiv and a journal.  It uses the `pdfpages` and `pgffor` latex packages.  

## Method

Place the following in the header of your main `manuscript.tex` file

    \usepackage{pdfpages} % include pdfs
    \usepackage{pgffor}   % for loops

    % A fix for revtex-pdfpages rotation bug 
    \makeatletter
    \AtBeginDocument{\let\LS@rot\@undefined}
    \makeatother

and include at the end of the document

    ...
    \bibliography{refs}


    \foreach \x in {1,...,N}
    {
    \clearpage
    \includepdf[pages={\x,{}}]{supplement.pdf}
    }

    \end{document}

where `N` should be replaced with the number of pages in the PDF file.

## Usage 
1. Generate `supplement.pdf` by running `pdflatex/bibtex` on `supplement.tex` to create a stand-alone PDF file
2. Run `pdflatex/bibtex` on `manuscript.tex` to produce the combined `manuscript.pdf` file.
3. Upload `manuscript.tex`, `manuscript.bbl` and `supplement.pdf` to the arXiv.

## TODO
- Determine a method to automatically calculate the number of pages of `supplement.pdf` within LaTeX
- Replace `pgffor` package with plain TeX loop
