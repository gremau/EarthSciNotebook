# Python tips

Python is a very powerful, high-level programming language that, when
combined with some numerical, scientific, and plotting packages, makes a
very powerful tool for scientific computing and data analysis (similar
to Matlab). Useful python extensions for this application are
[NumPy](http://numpy.scipy.org/),
[SciPy](http://www.scipy.org/),[Matplotlib](http://matplotlib.sourceforge.net/),
[IPython](http://ipython.org/), and
[SciKits](http://scikits.appspot.com/scikits). This page
collects some general tips on developing Python code.

 **See also:\*\* [NumPy tips](procedures:numpytips), the
        [IPython page](procedures:ipython), and the Python
        section of [the general programming
        page](procedures:programming#python).

## Installing Python packages

Installation of packages from [PyPI](http://pypi.python.org)
(the Python Package Index) is generally done with easy\_install, which
is part of \*\*python-setuptools\*\*. Also install \*\*python-dev\*\* so
that new packages can be built locally.

Then:

` easy_install [packagename]`

 **NOTE\*\* that easy\_install will no longer work with Python 3.0
        and
        [pip](http://www.pip-installer.org/en/latest/index.html)
        will have to be used.

## The datetime module

Python's *datetime* module suplies the core functionality for handling
datetime objects. Descriptions of its core classes, and their attribute
and methods are briefly covered below, or see Python's more extensive
[Datetime library
reference](http://docs.python.org/library/datetime.html).

` * `*`dt.date(year,` `month,` `day)`*\
`   * `*`dt.date.min`*` and `*`dt.date.max`*` give the minimum and maximum possible dates
`   * `*`dt.date.year`*`, `*`dt.date.month`*` and `*`dt.date.day`*` return the attributes
`   * `*`date.strftime(format)`*` - returns a string representing the date, controlled by an explicit format string
`   * `*`date.toordinal()`*` - returns the proleptic Gregorian ordinal of the date, where January 1 of year 1 has ordinal 1.
` * `*`dt.time(hour[,` `minute[,` `second[,` `microsecond[,`
`tzinfo]]]])`*\
`   * all the attributes are optional and the `*`tzinfo`*` attribute (which defines timezone, time offsets, etc) can be "None"
`   * similar methods to those in `*`dt.date`*\
` * `*`dt.datetime(year,` `month,` `day[,` `hour[,` `minute[,`
`second[,` `microsecond[,` `tzinfo]]]]])`*\
`   * Contains all the info from a `*`date`*` and a `*`time`*` object.
`   * year, month, day are required, tzinfo can be 'None'.
`   * two class method contstructors are important: 
`     * `*`datetime.combine(date,`
`time)`*` combines a date and a time object into a datetime.
`     * `*`dt.datetime.strptime(date_string,`
`format)`*` - returns a datetime corresponding to date_string, parsed according to format.
`   * Similar instance methods to `*`date`*` and `*`time`*` objects (can call strftime, toordinal, etc.)
` * `*`dt.timedelta([days[,` `seconds[,` `microseconds[,`
`milliseconds[,` `minutes[,` `hours[,` `weeks]]]]]]])`*\
`   *  Represents a duration, the difference between two dates or times.`

### Using strptime()and strftime()

The datetime.strptime() class method creates a datetime object from a
string representing a date and time and a corresponding format string.
date.strftime(format) returns a string representing the date, controlled
by an explicit format string. To format these inputs and outputs use the
"%field" formatting codes. A list of the codes is
[here](http://docs.python.org/library/datetime.html#strftime-strptime-behavior)

## Debugging code

#### Python debugger (pdb)

More on this module
[here](http://pythonconquerstheuniverse.wordpress.com/category/python-debugger/).
The Python library page is
[here](http://docs.python.org/library/pdb.html).

~~~

1.  import the pdb module

import pdb

1.  insert this into code at line x to start debugger at line x

pdb.set\_trace()

1.  as the code runs it will stop and enter the debugger at line x
2.  leaving you at the pdb prompt

(Pdb)

1.  once in interactive mode several commands can be issued

n # execute the next line p var1, var2, var3 # print the value of
variables c # exit interactive debugger and continue running program l
# list area of program where you currently are s # step into a
subroutine (function call on that line) r # if in a subroutine,
continue until returned to original subroutine call q # crash out of
debugging

1.  if there are variable assignments or other changes to be made they
    can be
2.  made at the debugger prompt and then tested by continuing the code

(Pdb) var1 = "bbb"

1.  An exclamation point tells pdb that what follows is a Python
    statement, not a pdb command.

(Pdb) !b = "BBB"

1.  It is also possible to set a breakpoint, (then continue to
    this breakpoint).

(Pdb) break function.py:4 ~~~

Other useful Pdb classes:

~~~

1.  run a file or statement interactively with the debugger

pdb.run('mymodule.test()')

1.  similar to *pdb.run* but returns the value of the expression

pdb.runeval(expression)

1.  calls the specified function and passes any specified arguments to
    it:

pdb.runcall(function[, argument, ...])

1.  performs postmortem debugging of the specified traceback

pdb.post\_mortem(traceback)

1.  performs postmortem debugging of the traceback contained in
    sys.last\_traceback:

pdb.pm()

~~~

#### Other useful debugging modules

IPdb
----

The IPython shell has its on debugging module, similar to Python's. See
the [IPython page](procedures:ipython) for more.

Code.interact()
---------------

code.interact() stops execution and gives you an interactive console to
examine the current state of your program. To use this function, simply
embed the following at the line were you want the console to start:

` import code; code.interact(local=locals())
` `

The resulting console inherits the local scope of the line on which
code.interact() is called. This enables you to check the current state
of your program to understand its behavior and make any necessary
corrections.

Logging
-------

Python has a logging module that allows the collection of various log
messages from within a running program. To start logging debug messages
it must be imported and configured to log DEBUG level messages:
~~~

` import logging
` # Log everything, and send it to stderr.
` logging.basicConfig(level=logging.DEBUG)
` 
` # Now, in the body of the program, you can log events like this:
` logging.exception("Something bad happened!")
` logging.debug("Finishing for loop")`

~~~
