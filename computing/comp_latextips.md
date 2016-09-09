# LaTeX tips

**See also:** [[comp_textfiles]], [[comp_pandoc]]

## General Resources

* [TexLive distribution](http://www.tug.org/texlive/)
* [TeX Stackexchange site](https://tex.stackexchange.com)
* [Short tutorial](http://www.math.uiuc.edu/~hildebr/tex/course/) geared to math students.
* [Harvard math dept. reference](http://www.math.harvard.edu/texman/)
* A simple [LaTeX pre-viewer](http://www.tlhiv.org/ltxpreview/) that can be used for code on this page.
* An [SE question](http://stackoverflow.com/q/193298/1282366) with lots of tips and best practices for LaTeX.

## Citations

Insert a citation with `\cite{citationID}`, where `citationID` is the
identifier in a BibTeX (.bib) bibliography file. The `.bib` is defined
somewhere in the LaTeX file with
`\bibliography{\~\\user...\\bibfile.bib}`. There are other, improved
implementations for citations, such as
[natbib](http://www.ctan.org/tex-archive/macros/latex/contrib/natbib).

Currently there is an error in the Zotero export filter for .bib files
(parentheses and brackets are sometimes reversed when abbreviations and
special characters are present). Open bibtex in vim and do:

    :%s/)\}/\})/c

### Citation Resources

* A [natbib reference sheet](http://merkel.zoneo.net/Latex/natbib.php).
* [Some tips](http://libguides.mit.edu/content.php?pid=55482&sid=406343#6) on using Zotero with BibTeX

## Making tables

It may be easier to make and format the table in a spreadsheet first,
and some spreadsheets can export tables directly to LaTeX format.
Gnumeric, and Libre Calc (using
[Calc2LaTeX](http://calc2latex.sourceforge.net/)) do a decent
job, but there will still be formatting to make it look nice. Once you
have some data to format into a LaTeX table, this is the traditional way
to do it:

```latex
\begin{tabular}{|c|c|c|}
\hline
A & B & C\\
\hline\hline
foo & bar & baz\\
\hline
zab & rab & oof\\
\hline
\end{tabular}
```

A better way is to use the
[Booktabs](http://www.tex.ac.uk/tex-archive/macros/latex/contrib/booktabs/ "wikilink")
package, and use something like this:

```latex
\begin{tabular}{ccc}
\toprule
A & B & C\\
\midrule
foo & bar & baz\\
zab & rab & oof\\
\bottomrule
\end{tabular}
```

## Mathematical typesetting

TeX/LaTeX excels at this. Mathematical statements or formulas are
generally placed between dollar signs. Here are a few resources:

-   <http://www.math.uiuc.edu/~hildebr/tex/course/intro2.html>

## Comments, TODOs, and other document annotations

Comments can be added to a document with the *%* signifying the
beginning of a comment. If a document is reviewed by another and they
add these types of comments, they will be picked up by a diff between
the original and the patch.

### A couple other ideas

* The [todonotes package](http://ctan.org/pkg/todonotes) places callouts (Word style) 
in the compiled document.

## Converting to Word/LO formats

* [This tex.se question](http://tex.stackexchange.com/q/4145) has some great ideas and links.
* There are other ideas in [this SE question](http://stackoverflow.com/q/615738/1282366)
