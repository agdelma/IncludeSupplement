# IncludeSupplement

A simple method for including supplemental materials files on the arXiv.

This repository includes information on how to include a supplemental materials file as a stand-alone PDF file when co-submitting a paper to the arXiv and a journal.  It uses the `pdfpages` and `pgffor` latex packages.  

## Method

Place the following in the header of your main `manuscript.tex` file

    \usepackage{pdfpages} % include pdfs
    \usepackage{pgffor} % for loops
    
    % Fix for a pdfpages rotation bug with revtex
    \makeatletter
    \AtBeginDocument{\let\LS@rot\@undefined}
    \makeatother
    
    % the name of the supplement PDF file
    \def\supplementfilename{supplement.pdf}
    
    % Determine the number of pages 
    % in the supplement file and store
    \pdfximage{\supplementfilename}
    \def\numbersupplementpages{\the\pdflastximagepages}
    
    % Are we submitting to the arXiv? 
    % Un-comment the appropriate line
    \newif\ifarXiv
    \arXivtrue 
    % \arXivfalse

and include at the end of the document

    ...
    \bibliography{refs}

    \ifarXiv
        \foreach \x in {1,...,\numbersupplementpages}
        {
            \clearpage
            \includepdf[pages={\x,{}}]{\supplementfilename}
        }
    \fi

    \end{document}

where `\numbersupplementpages` is the automatically determined number of pages in the PDF file.

## Usage 
1. Generate `supplement.pdf` by running `pdflatex/bibtex` on `supplement.tex` to create a stand-alone PDF file
2. Run `pdflatex/bibtex` on `manuscript.tex` to produce the combined `manuscript.pdf` file.
3. Upload `manuscript.tex`, `manuscript.bbl` and `supplement.pdf` to the arXiv.

## TODO
- Replace `pgffor` package with plain TeX loop
