# Data analysis programming: general info

This page collects info and links (to this site or others) useful in
data analysis programming, including resources for various languages,
editors, or testing tools, and notes/tips for using them effectively.

## General techniques and conventions

Notes about data analysis techniques/conventions, independent of
language/interface.

  * [Sensor data tips](comp_sensordata_tips.md) - collected notes on working with continuous sensor timeseries (from dataloggers, SNOTEL sites, etc.
  * [Data analysis workflow](comp_data_analysis_workflow) - Greg's notes on collecting, storing, and moving data through the analysis process.

## Text editing and data file handling

**[VIM](http://www.moolenaar.net/vim.html) is a great text editor**. Below are a few resources on using it effectively.

  * A fairly complete [Vim commands cheatsheet](http://bullium.com/support/vim.html).\
  * [The Vim tips wiki](http://vim.wikia.com/wiki/Vim_Tips_Wiki)
  * [Seven Habits](http://www.moolenaar.net/habits.html) for effective text editing.

**An excellent general overview of text/data file handling** in  a Unix environment is provided by Unix for Poets, by Kenneth Ward Church. PDFs of this are all over the internet.

**Other useful resources (including some on this wiki):**

  * [Textfile tips](comp_textfiles) - various command-line ways of manipulating text.\
  * [Shell scripting tips](comp_shellscripts), including Unix shell scripts and useful utilities.\
    * [BASH hackers site](http://wiki.bash-hackers.org/doku.php) is helpful.\
    * [Shell scripting tutorial](http://www.vectorsite.net/tsshell.html) by Greg Goebel/Public Domain\
  * [Vim tips](comp_vimtips) - tips for using the Vim editor.\
  * sed is a text stream editor great for pattern matching and replacing\
    * See [this tutorial](http://www.grymoire.com/Unix/Sed.html)
    * [This page](http://sed.sourceforge.net/sed1line.txt) gives great one-line examples.\
  * [Awk](comp_awk) is also very useful for manipulating text files.\
    * [The awk gateway](http://awk.info/)
    * [Awk one-liners explained part
one](http://www.catonmat.net/blog/awk-one-liners-explained-part-one/)
    * [Awk one-liners explained part
two](http://www.catonmat.net/blog/awk-one-liners-explained-part-two/)
    * [Awk
tutorial](http://www.vectorsite.net/tsawk_1.html) by Greg Goebel/Public Domain

## Python

Python is a high-level, open-source programming language that, when
combined with some numerical, scientific, and plotting packages, makes a
very powerful tool for scientific computing and data analysis (on par
with Matlab). Useful Python extensions for scientific computing are:

 - [NumPy](http://numpy.scipy.org/) - provides n-dimensional array objects and other useful numeric extensions to Python\
 - [SciPy](http://www.scipy.org/) - provides a number of high-level mathematical tools for use in scientific computing (integration, optimization, fourier transforms...etc
 - [Matplotlib](http://matplotlib.sourceforge.net/) - a plotting library that provides publication quality plots and plotting routines that are similar to Matlab's.\
 - [IPython](http://ipython.org/) - an interactive shell that is designed to work well with NumPy, SciPy, and Matplotlib.\
 - [SciKits](http://scikits.appspot.com/scikits) - add on toolkits that complement SciPy (various statistical models, timeseries analysis, machine-learning, image processing, etc.
 - The [pandas library](http://pandas.pydata.org/) - provides high-performance, easy-to-use data structures (like data frames) and data analysis tools that sit on top of NumPy. 

### Resources

  * [Official links](http://www.python.org/doc/) to Python documentation, including tutorials HowTo's and these:\
    * [Python Language Reference](http://docs.python.org/reference/) - describing the syntax and core semantics of the language.\
    * [Python Standard Library](http://docs.python.org/library/) - describing the standard library (modules, functions, etc) distributed with Python.\
  * Coding in python should follow the [Python Style Guide](http://www.python.org/dev/peps/pep-0008/).\
  * [Official documentation](http://docs.scipy.org/doc/) for NumPy/SciPy, and [additional documentation](http://www.scipy.org/Additional_Documentation]] (tutorials, etc.
  * [PyPlot documentation](http://matplotlib.sourceforge.net/api/pyplot_api.html) for the Matlab-like plotting framework in matplotlib.\
  * [The Python Wiki Vim page](http://wiki.python.org/moin/Vim) and [this blog
entry](http://dancingpenguinsoflight.com/2009/02/python-and-vim-make-your-own-ide/) give some interesting tips about using vim as a python source editor.\
  * [Spyder](http://code.google.com/p/spyderlib/) is a MATLAB-like IDE for python (Numpy and Matplotlib enabled) that could be an alternative to VIM/[IPython](comp_ipython))

**Python (and its scientific extensions) have a large user/developer community supporting them. These are some forums that might be helpful:**

  * [http://www.scipy.org/Mailing_Lists](http://www.scipy.org/Mailing_Lists)
  * [http://old.nabble.com/Scipy-User-f33045.html](http://old.nabble.com/Scipy-User-f33045.html)

### Notes

Collected notes, tips, and tricks for using any of the Python tools
above.

  * [Python package index](http://pypi.python.org/pypi) - an index of many add-on tools discussed in this wiki. Installing them is covered [here](comp_pythontips).\
  * [Ipython](comp_ipython) - notes on using IPython.\
  * [Python tips](comp_pythontips) on debugging, code structure, and other aspects of Python development.\
  * [NumPy tips](comp_numpytips) - Various notes on using the NumPy package.

## MATLAB (and clones)

[MATLAB](http://www.mathworks.com/products/matlab/) is a
proprietary programming language and IDE that is widely used in
scientific and engineering computing.

### Resources

  * [Official MathWorks documentation](http://www.mathworks.com/help/techdoc/)
  * [Function reference](http://www.mathworks.com/help/techdoc/ref/f16-6011.html)
  * [MATLAB Central](http://www.mathworks.com/matlabcentral/) - the official user/developer community, including a [file
exchange](http://www.mathworks.com/matlabcentral/fileexchange/).\
  * [Kluid forums](http://www.kluid.com/mlib/index.php) has matlab and octave forums.

### Clones of Matlab

There are a bunch of free/open-source clones of Matlab that have various
levels of syntax compatibility.

  * [GNU Octave](http://www.gnu.org/software/octave/) - generally very compatible with Matlab, though some functions are missing.\
  * [SciLab](http://www.scilab.org/)
  * [FreeMat](http://freemat.sourceforge.net/)

### Notes

  * [Tips and tricks for using Matlab](matlabtips)

## R

R is a free, open-source software environment for statistical computing
and graphics.

  * [R-project homepage](http://www.r-project.org/index.html)
  * [R manuals](http://cran.r-project.org/manuals.html)
  * [R wiki](http://rwiki.sciviews.org/doku.php)

### Notes

  * [Tips and tricks for using R](rtips)
  * [knitr](https://github.com/yihui/knitr#readme) - a nice report generating engine for R

## Math and Stats tools

Many toolboxes are available, either standalone or in Python, R, and
Matlab, for math and statistical applications. See the [math toolbox page](math_toolboxes.md) page.

## Testing data analysis functions

Code used in data analysis can perform fairly complex operations on
datasets and generate output that may be significantly changed from the
original data. The code itself can also be fairly complex and its actual
function may be difficult to discern just by reading the code or looking
at the data. It is important to verify that the result of running this
code is what is expected and that the output is accurate. Writing test
functions that call data analysis code and analyze their output is a
useful way to do this.
