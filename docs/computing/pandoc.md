# Pandoc

[Pandoc](http://johnmacfarlane.net/pandoc/) is a utility to
convert text markup formats (Markdown, reStructuredText, LaTeX, etc) to
a variety of other document formats (.doc, .pdf, HTML, etc). Pandoc also
provides its own extension of Markdown syntax (details
[here](http://johnmacfarlane.net/pandoc/README.html#pandocs-markdown)).

Be sure to install:

* pandoc
* pandoc-data
* pandoc-citeproc (for citations)

## Basic use for creating PDFs

`pandoc -o` writes output to the file following the `-o`, with
formatting based on the file extension. For example, the following
command creates a pdf file from a text file (via pdflatex):

    pandoc cv_master.txt -o cv_master.pdf

There are other options for specifying input and output files or
formats, but this is the simplest.


## PDF formatting options

The output formatting of a pdf document can be set either at the
commandline, or by using a header or template file during the
conversion.


### Passing variables

The `-V` (or `--variable`) option changes formatting, fonts, or other
settings during a pandoc conversion.

    pandoc cover_master.txt -V geometry:margin=1.5in -o  cover_master.pdf
    # create pdf with 1.5in margins

Other variables that can be passed with `-V` are
[here](http://johnmacfarlane.net/pandoc/README.html#templates)

Note that some of these variables, such as geometry, can also be passed in a YAML metadata block. See [here](http://pandoc.org/MANUAL.html#extension-yaml_metadata_block) for details.


### Include in header

When `-s` (or `--standalone`) is used, pandoc adds the header and footers
needed for a standalone document in the output format. To see the
default template used, type `pandoc -D FORMAT`. There are a couple of
ways to change what is in this header. The `-H=FILE`
(`--include-in-header=FILE`) option can include special formatting
information contained in FILE with the default header. This can be
useful when adding LaTeX formatting commands to the intermediate .tex
file before creating the pdf.

    pandoc cv_master.txt -H '/path/to/header/' -o cv_master.pdf


### Custom document templates

A custom template for the output document header can also be specified
using `--template=FILE`, where FILE is the custom template. If this
option is specified, pandoc first looks in the current directory, then
the user template directory (`$HOME/.pandoc/templates`), and then in
the default template directory (`/usr/share/pandoc...`). Templates
should end with an extension for the output format (.latex, .html, etc).
To create a new template, copy the default for the given output format
using:

    pandoc -D latex > newtemplate.latex

This is good practice when starting a new project because default
templates are updated in new versions of pandoc. The template can then
be modified and then used in converting the document using:

    pandoc manuscript_1.markdown --template=newtemplate.latex --bibliography=SNOTELsoildata.bib -o manuscript_1.pdf

You can put useful stuff in these templates, like setting margin widths,
using packages, etc. A couple I use for pdfs of journal articles are:

    \usepackage[margin=1in]{geometry}
    \usepackage{textcomp} % provides \textdegree


### Other formatting

                 Option | Result
----------------------- | -----------------------------------------------------------------------------------------------------------
`--toc`                 | Automatically create a table of contents
`--toc-depth`           | Specify the header levels to be used in table of contents (implies --toc)
`--reference-odt=FILE`  | Use the FILE stylesheets as a template for .odt output. Best if FILE was created with pandoc, then modified.
`--reference-docx=FILE` | Use the FILE stylesheets as a template for .docx output.
`--latex-engine=ENGINE` | Choose the pdflatex|lualatex|xelatex interpreters, needed for some formatting in pdf files.

## Citations and bibliographies

Pandoc is capable of including citations from an associated
bibliographic database (usually a BibTex file). Citations in a pandoc
markdown file look like this: `[@citationid]` , where `citationid` is
defined in the associated .bib file. To convert a pandoc file with
citations, run:

    pandoc paper1_draft.markdown -o paper1_draft.pdf --bibliography hiddencanyon.bib

A bibliography will be automatically written after the *References*
heading, if it is included. Citation and bibliography formatting can be
specified with `--csl=FILE`, where `FILE` is a .csl file (found at
<http://citationstyles.org>). Natbib and biblatex can be used in LaTeX
output (pdf) by including them as commandline options.

## Working directly with LaTeX

Pandoc markdown is a nice way to draft LaTeX documents. Pandoc markdown can be
rendered to TeX (`-o document.tex`), or rendered as a PDF via `pdflatex`
(`-o document.pdf`). Raw TeX and LaTeX can be included in a markdown
document and it will be passed to the pdflatex writer. For more info on
LaTeX/Tex systems see [this page](latex_notes.md).

### Citations

    This is a citation from Smith \cite{smith.2013}

The citation should be output in BibTex format FIXME// - havent gotten
this to work yet//. Inline TeX placed between *\\begin* and *\\end* tags
will be interpreted as LaTeX instead of markdown, and will be ignored in
non-LaTeX output formats.

### Math mode

TeX math can be used by putting it between dollar signs. One dollar sign
(each side) for inline mode, and two for display math. Most LaTeX math
mode symbols are also transferred to other output formats. For example,
rendering HTML documents with greek characters (such as $\theta$)
will result in unicode (default) greek characters in the rendered HTML.
There are also options for using MathML, MathJax, if this doesn't work.

## Errors with unicode special characters

Pandoc will pass unicode characters in a document to `pdflatex` that it may 
not know how to display. This is pretty common with greek characters that are 
used outside of math mode. In this case it is probably best to use the Xetex
interpreter instead. This can be specified by sending `--latex-engine=xelatex`
to pandoc. Of course, Xetex must be installed, which is most easily done
by installing the full TexLive distribution (large).
