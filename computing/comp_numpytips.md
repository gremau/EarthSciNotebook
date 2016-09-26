# NumPy tips

NumPy gives array classes and other tools useful in data analysis.
Official documentation is [here](http://docs.scipy.org/doc/).

 **See also:** [Python tips](procedures:pythontips),
        [General programming](procedures:programming) pages.

## Date/time objects and arrays

### Python *datetime* module

Python's *datetime* module suplies the core functionality for handling
datetime objects. Descriptions of its core classes, and their attribute
and methods are briefly covered
[here](procedures:pythontips#The_datetime_module), or see
Python's more extensive [Datetime library
reference](http://docs.python.org/library/datetime.html).

#### Input/output datetime arrays with NumPy

The datetime.strptime() class method creates a datetime object from a
string representing a date and time and a corresponding format string.
date.strftime(format) returns a string representing the date, controlled
by an explicit format string. To format these inputs and outputs use the
"%field" formatting codes. A list of the codes is
[here](http://docs.python.org/library/datetime.html#strftime-strptime-behavior).
When reading a datafile, a column of formatted dates can be read in in
the following way. 

~~~
# First define a function that converts the formatted date to a datetime object
def datestr2num(s):
    return datetime.datetime.strptime(s, "%Y/%m/%d")

#then, this function can be passed as a converter argument in a genfromtxt() call
datetxt = genfromtxt(datapath + 'swe.txt', skiprows=2, delimiter=',',
                     usecols=(0,), converters={0: datestr2num})
~~~

:!: cant seem to get the same thing to work with loadtxt for some
    reason

#### Datetimes in NumPy itself

New in NumPy 1.7 is a core datatype for datetime objects
called*datetime64*. It should implement similar functionality as above,
but a little more automatically -
see[here](http://docs.scipy.org/doc/numpy/reference/arrays.datetime.html).

## Masking invalid/missing values in arrays

One of the biggest tasks in getting data ready for analysis is
identifying and "masking" data values that are missing or invalid for
some reason. These values can be handled in Numpy arrays using a number
of approaches.

#### Index arrays

Numpy arrays can always be indexed with other NumPy arrays (as long as
they have valid indices). If the index number of bad or missing data is
known, the array can always be indexed using another numpy array that
excludes the indices of invalid data.

~~~
In [0]: arange(10,1,-1)

Out[0]: array([10, 9, 8, 7, 6, 5, 4, 3, 2])

In [1]: x = arange(10,1,-1)

In [2]: x

Out[2]: array([10, 9, 8, 7, 6, 5, 4, 3, 2])

In [3]: x[array([0, 1, 2, 3, 4, 5])]

Out[3]: array([10, 9, 8, 7, 6, 5])
~~~

Boolean arrays can also be used to index data arrays.
A boolean array of the same dimension as the data array is created by
applying a logical statement. This boolean array can then be used as an
index.

~~~
In [4]: test = x>=5

In [5]: test

Out[5]: array([ True, True, True, True, True, True, False, False, False], dtype=bool)

In [6]: x[test]

Out[6]: array([10, 9, 8, 7, 6, 5])
~~~

More on using boolean index arrays
[here](http://docs.scipy.org/doc/numpy/user/basics.indexing.html#boolean-or-mask-index-arrays)

#### Nan values

Adding Nan to an array can mask or mark invalid values, and these values
can then be left out of calculations in various ways.
~~~
#change bad decagon sm sensor data (-6999) to nan
test = (m == -6999) m[test] = nan
~~~

*isnan* can be used to locate Nan values in an array by creating a boolean array of the same dimensions. True values are Nans.

~~~
In [0]: b = arange(10.)

In [1]: b[2] = nan

In [2]: b

Out[2]: array([ 0., 1., nan, 3., 4., 5., 6., 7., 8., 9.])

In [3]: isnan(b)

Out[3]: array([False, False, True, False, False, False, False, False, False, False], dtype=bool)
~~~

It is important to note that in most calculations on an an array
containing Nan values, the Nan value will be propagated to the result.
This can be avoided by using boolean arrays (such as from *isnan*) to
remove Nan values from the calculation. There are also a number of
functions that will perform operations on an array while leaving out nan
values (**nansum(), nanmax(), nanmin(), etc.**).

~~~
In [4]: sum(b)

Out[4]: nan # should be 43, but the nan propagates to the answer

In [5]: nansum(b) # this leaves out the nan 

Out[5]: 43.0

In [6]: sum(b[~isnan(b)]) # this also leaves out the nan

Out[6]: 43.0
~~~

#### Masked Arrays

Masked arrays are a separate module that must be imported (numpy.ma).
This module allows creation of masked arrays that consist of an ndarray
and a boolean "mask" array of the same dimensions. Data (in the ndarray)
that is marked with a False value in the boolean mask are considered
valid, while True values denote a missing or invalid value. Operations
on the masked array (np.sum, np.mean, etc) don't take the invalid data
into account. In this sense it is similar to using a logical test array
to mask values in Matlab, but once the mask is created, the masked array
can be used like a normal array (without continual explicit use of the
mask).

~~~ In [7]: import numpy.ma as ma

In [8]: b # start with an array containing one nan - see lines 0 and 1 in section above 

Out[8]: array([ 0., 1., nan, 3., 4., 5., 6., 7., 8., 9.])

In [9]: c = ma.array(b, mask=isnan(b))

In [10]: c

Out[10]: masked_array(data = [0.0 1.0 -- 3.0 4.0 5.0 6.0 7.0 8.0 9.0],

           mask = [False False  True False False False False False False False],
     fill_value = 1e+20)
~~~

Once the masked array is created, the data and the mask are both
accessible using the built in attributes **.data** and
**.mask**. **ANY** functions and methods that operate on arrays
operate the same on masked arrays, but the masked values are left out of
the calculation.

~~~
In [11]: c.data

Out[11]: array([ 0., 1., nan, 3., 4., 5., 6., 7., 8., 9.])

In [12]: c.mask

Out[12]: array([False, False, True, False, False,
False, False, False, False, False], dtype=bool)

In [13]: c.sum()

Out[13]: 43.0

In [14]: mean(c)

Out[14]: 4.7777777777777777

In [15]: sum(c.data) 

Out[15]: nan
~~~

There are other ways to
construct masked arrays, notably *masked_where* and its aliases
(*masked_greater, masked_equal, masked_inside*, etc). In addition,
the masked or unmasked data can be accessed using the mask itself (or
~mask). 

~~~
In [16]: d = ma.masked_where(a>=5, b)

In [17]: d

Out[17]: masked_array(data = [0.0 1.0 -- 3.0 4.0 -- -- -- -- --],

           mask = [False False  True False False  True  True  True  True  True],
     fill_value = 1e+20)

In [18]: d[~d.mask]

Out[18]: masked_array(data = [0.0 1.0 3.0 4.0],

    mask = [False False False False],fill_value = 1e+20)

~~~

 **Other things to note:**

The mask argument in *ma.array* must be convertible to a boolean array
of the same size as the input data array. Adding the *fill_value=x*
argument will fill in masked values with x. Other arguments for
contstructing arrays can be found [ma.array function](http://docs.scipy.org/doc/numpy/reference/generated/numpy.ma.array.html#numpy.ma.array)
description. As a subclass of the numpy.ndarray class, the
ma.MaskedArray class inherits all its attributes and methods, plus adds
a few others ([shown here](http://docs.scipy.org/doc/numpy/reference/maskedarray.baseclass.html#numpy.ma.MaskedArray)).

Lots more info on working with masked arrays: [Masked arrays in the NumPy Reference](http://docs.scipy.org/doc/numpy/reference/maskedarray.html)

#### NA-Masked arrays

There is a new NA-masked array introduced in Numpy 1.7 that puts
NA-masking directly in the core (instead of a separate module).

Details
[here](http://docs.scipy.org/doc/numpy/reference/arrays.maskna.html).
