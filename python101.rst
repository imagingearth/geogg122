
=====================================
Introduction to programming in Python
=====================================

Python
======
Python is a high-level programming language that is suitable for a range of tasks in scientific computing.
Relevant features include:
- it is automatically compiled and executed
- code is *portable* provided you have the appropriate Python modules.
- for compute intensive tasks, you can easily make calls to methods written in (faster) lower-level languages such as C or FORTRAN
- there is an active user and development community, which means that new capabilities appear over time and there are many existing extensions and enhancements easily available to you. 

We have provided `some instructions <pythonhelp.html>`_ that should help you set up your own Python installation on your own computer if you need or want to, but you will also easily find information on the web. You will also find other introductory (and more advanced) materials on the web (e.g. `this beginners guide <http://wiki.python.org/moin/BeginnersGuide>`_). Other useful resources include:

- `Python documentation <http://www.python.org/doc/>`_
- `The Python home Web site <http://www.python.org/>`_
- `Python FAQ <http://www.python.org/doc/FAQ.html>`_
- `Advanced Scientific Programming in Python <https://python.g-node.org/wiki/schedule>`_

In this session
---------------

In this part of the session, we will cover:

[`boolean`_] [`dict`_] [`del`_] [`files`_] [`float`_] [`for`_] [`integer`_] [`ipython`_] [`lists`_] [`modulo`_] [`print`_] [`range`_] [`strings`_] [`type`_] [`variables`_] [`xrange`_]

which is a good deal of the main Python builtin types. You can find more detailed information on this `from docs.python.org <http://docs.python.org/library/stdtypes.html>`_.


Getting started
---------------

.. _ipython:

We will start by using an interactive Python session using ``ipython``. You may already have personal preferences in this matter, and may well wish to use `IDLE <http://docs.python.org/library/idle.html>`_ (Python's Integrated DeveLopment Environment) or some other python shell/environment. It is up to you, but we will assume the use of ``ipython`` from a Unix shell here. 

You should start up ``ipython``, e.g. from Unix by typing::

    berlin% ipython

which should result in the prompt::

    In [1]:

You can now type Python 'commands' at the prompt which will be executed when you hit return. If you just use the standard Python interface (i.e. just typing ``python``), the prompt will be:

    >>>

so we will use this to indicate the prompt. Actually, not every command is executed when you hit return, as sometimes we need to use multiple lines. In this case, the prompt will be::

   ...:

in ``ipython`` or::

   ...

in ``python``. We will use ```...`` in these notes to indicate the line continuation prompt. Obviously, you should not actually type in the prompt parts in these examples.

To exit from the ``ipython`` session, type ``^D`` (CNTRL and D), the standard end of file (EOF) marker.


Data types
==========

.. _strings:

String data type
----------------
Datatypes are ways that we represent information in the language we are using. Really these are just particular types of classes. One core example is the ``string`` datatype, which we can create within single `'` or double `"` quotes::
  
    >>> 'hello world'
    'hello world'
    >>> "hello again"
    'hello again'
    >>> ''' A string 
    ... that goes over multiple lines.
    ... '''

.. _variables:

An important concept in programming is the `variable`. This is the basic way in which we can 'store' information for later manipulation and use. You set the 'contents' of a variable using an equals ``=`` symbol, as you might expect in most languages::

    >>> hw = 'hello world'

.. _print:

Here, we could use the method ``print`` to explicitly print the value of the string that we have assigned to the variable ``hw``::

    >>> print hw 
    hello world

A method is something that we can apply to a variable, which will typically do something with it, in this case, print out its value.
The string datatype has a number of 'built in' methods that can be used to manipulate string data. Full information on this can be found by typing::

    >>> help(str)

which will give you detailed information on what you can do with a string. Python documentation is also available online, e.g. at `www.python.org <http://www.python.org/doc/current/lib/string-methods.html>`_. 

We can combine strings with the ``+`` operator, e.g.::
 
    >>> this =  'hello' + 'world'
    >>> print this
    helloworld

You will have noticed from this that no space is added automatically, so you might prefer::

    >>> print 'hello' + ' world'
    hello world

Another way of generating strings is to use a formatting statement, e.g.::

    >>> print 'This is the %s code %s ever wrote'%('first','I')
    This is the first code I ever wrote

The ``%s`` symbol here stands for 'string' and expects a string argument after it (in the brackets, after the ``%`` symbol). Importantly, we could have used variables here and inserted their values into the string:

    >>> whichOne = 'first'
    >>> mySelf = 'I'
    >>> print 'This is the %s code %s ever wrote'%(whichOne,mySelf)
    This is the first code I ever wrote
 
Some examples of methods for strings then::

    >>> hw = 'hello world'
    >>> hw.count('l')
    3
    >>> hw.find('l')
    2
    >>> hw.find('lo')
    3
    >>> hw.isdigit()
    False
    >>> hw.replace('world','everyone')
    'hello everyone'
    >>> hw.split()
    ['hello', 'world']

Exercise
~~~~~~~~

type the following:

.. literalInclude:: python/ex1.py


You don't need to be too worried about the details of this code right now, just note that it has a line ``print line`` where ``line`` is some text read from you typing at the keyboard (``stdin``).

If you want to follow through what the code does, first not the indentation in the code, which clafiries where loops and conditional statements start and end.
    
The code will read lines from ``stdin`` (e.g. the keyboard) and print them out to ``stdout`` (the terminal) until you enter a blank line or ``q``. The code contains some new elements. First, we see that we can ``import`` other libraries or modules with the command ``import``:

.. literalInclude:: python/ex1.py
    :lines: 1-1

Next we see a call to a method ``sys.stdin.readline()`` and the use of the string method ``strip()`` (see if you can work out the purpose of the call to ``strip()``) then we use a ``while`` contruct to form an infinite loop (``while 1:`` or perhaps more clearly ``while True:``):

.. literalInclude:: python/ex1.py
    :lines: 2-3
.. literalInclude:: python/ex1.py
    :lines: 10-10


With just that code, the loop will continue indefinitely, setting the variable ``line`` to a line of data from ``stdin``, so we put in a break condition:

.. literalInclude:: python/ex1.py
    :lines: 4-5

so that if the (stripped) line is blank or just the character ``q``, we will ``break`` from the ``while`` loop. 

Another interesting feature is the code around the ``try`` statement:

.. literalInclude:: python/ex1.py
    :lines: 6-9    

which will attempt to print the contents of the variable ``line``. If this fails for any reason, we trap the exception and just continue on (``pass`` statemant).

Other than that, all the code does is to print out whatever you put in the line on ``stdin``. 

The exercise is to modify the code so that it replaces every time you type 'windows' with 'unix'. As a test, if you type in::

    If you are to install windows be aware that they need to comply with Building Regulations.

It should respond with::

    If you are to install unix be aware that they need to comply with Building Regulations.

which doesn't make a lot of sense, but illustrates the point. If you have done that easily, try to make your code work with different capitalisation (e.g. Windows -> Unix, windows -> Unix).

.. _boolean:

Boolean data type
-----------------

The Boolean data type is used for logical operations, for example::

    >>> this = True
    >>> that = False
    >>> type(this)
    bool
    >>> this and that
    False
    >>> this or that 
    True
    >>> not this or that
    False

These are just simple logical statements. Make sure you understand these basic operations, as we will use logic considerably later.

Exercise
~~~~~~~~

work out what::

    >>>  (s == 'star' and 'bat') or s

does, where ``s`` can be any data type, but might most easily be a string here. 

Hint: the ``==`` is an equivalence test, so ``s == 'star'`` will return ``True`` if ``s`` is the string ``star`` and ``False`` otherwise.

.. _lists:

Lists
-----

.. _type:

A list is an important data type as it allows us to group together objects of the same or different types. If we want to confirm what the datatype of something is, we can use the method ``type``::

    >>> type('1 2 3')
    str
    >>> type('1 2 3'.split())
    list

We can form a list using square brackets ``[]``, e.g.::

    >>> thisList = [ 1, 2, '3', '4', '5']
    >>> type(thisList)
    list
    >>> print thisList 
    [1, 2, '3', '4', '5']
    >>> print thisList[0]
    1
    >>> print type(thisList[0])
    <type 'int'>
    >>> print thisList[0:2]
    [1, 2]
    >>> print thisList[0:4:2]
    [1,'3']
    >>> print thisList[-1]
    5
    >>> print thisList[:-3]
    [1,2]
    >>> print thisList[-3:]
    ['3', '4', '5']

From these examples, we learn several things about lists. 

- First, we can express a list with square brackets containing comma separated values. 
- We can refer to an element in the list using square brackets on the list variable (e.g. ``thisList[0]``).
- We note that the counting system is 0-based, i.e. the *first* value in a list is ``thisList[0]`` (**not** ``thisList[1]`` as it would be in a one-based language)
- We can refer to list indices counting from the *end* of the list using negative numbers (so ``thisList[-1]`` is the last element in the list, ``thisList[-2]`` is the second to last etc.)
- We can refer to a range of values in a list using a colon ``:`` separator, e.g. ``thisList[0:2]`` is list elements 0 to 2 in steps of 1 (N.B. not including the last value, so it means 'from 0 up to but not including 2 in steps of 1'). The example ``thisList[0:4:2]`` involves steps of 2, clearly.
- In list ranges, the start, end or step can be implicit (as in ``thisList[:-3]`` which is equivalent to ``thisList[0:-3:1]``)
- A list data type can contain different data types: the first two elements in the list here are in fact integer number representations (``type(thisList[0]) == int``) whereas the others are of data type string (``str``).

You should generate your own list and make sure you appreciate these features of manipulating lists.

A few useful operators (see ``help(list)`` for more details)::

    >>> list = ['twinkle', 'little']
    >>> list.insert(0,list[0].capitalize())
    >>> list.append('star')

Here, we see how we can set up a list (of strings here, but lists can contain elements of any type). When you type these commands, check what value the variable you are setting or modifying becomes after each command, and make sure you understand why this is so.

Another way of forming list here would be::

    >>> list = ['twinkle']*2 + 'little star'.split()

which demonstrated the ``*`` and ``+`` operators for lists.

A useful logical statement might be::

    >>> s = list[0]
    >>> (s == 'star' and 'bat') or s


.. _for:


that does an operation with ``star`` and ``bat``. See if you can work out what it is doing. You can see its impact over the whole list by::

     >>> nlist = [(s == 'star' and 'bat') or s for s in list]

Importantly, here we see a looping structure: ``for s in list``. The simplest way to demonstrate this is::

    >>> for s in list:
    ...    print s
    twinkle
    twinkle
    little
    star

If we now put the logic statement in the loop::

    >>> for s in list:
    ...    this = (s == 'star' and 'bat') or s
    ...    print this

we can get some understanding of its operation. We can demonstrate a few other list operators::

    >>> list = (['twinkle']*2 + 'little star'.split())
    >>> str1 = "How I wonder what you are"
    >>> list.extend(str1.split())
    >>> nlist = [(s == 'star' and 'bat') or s for s in list]
    >>> nlist.remove('you')
    >>> nlist.insert(-1,"you're")
    >>> nlist.pop(-1)
    "are"
    >>> nlist.append('at')
    >>> print len(nlist)
    10
    
    
Note the use of ``"`` to form a string where the string contains ``'``` in ``"you're"``.
Other than that, see if you can follow what the various list methods are doing to the string (you can print what is happening at each stage). 


Exercise
~~~~~~~~

Examine the help pages for the string method ``join``, noting that a list is a 'iterable' (i.e. something you can iterate over) and show how it can be used to join the elements of ``nlist`` created above into `a single string`_.

.. _integer:


Integers
--------

We briefly came across the integer data type above. It is important to appreciate the difference between a string representation, e.g. ``'1'`` and a numerical representation such as an integer ``1``. In essence, we can do numerical operations on the latter, but not the former. A good example of this is::

    >>> '1' + '1'
    '11'
    >>> 1 + 1
    2

The first makes use of ``+`` to concatenate two strings, and results in the string ``11``. The second uses the ``+`` operator to perform the numerical operation 'plus' to the two integer numbers. Integer arithmetic proceeds as you would expect it to, but you should note that the result of numerical operations on integers is another integer, e.g.::

    >>> i = 1
    >>> i += 1
    >>> i = i + 1
    >>> i *= 2
    >>> i = i/2
    >>> i = i**3
    >>> i /= 9
    >>> print i
    3
    >>> print i/2
    1

.. _modulo:

So, 3/2 in integer type is 1. This is clearly involving rounding down. The remainder from such arithmetic can be found with the modulo operator (if needed)::

    >>> print 14/3,14%3
    4 2

which tells us that 14 is 4 * 3 + 2.

We can include integers in string formatting with a ``%d`` symbol::

    >>> i = 42
    >>> print 'The answer is %d'%(i)
    The answer is 42

We could also have converted the integer to a string representation using ``str()``::
 
    >>> i = 42
    >>> print 'The answer is still %s'%(str(i))
    The answer is still 42

Exercise
~~~~~~~~

Write some lines of code that converts an integer in base 10 to a representation in another base (e.g. 2).

.. _float:

Floating Point Numbers
----------------------

A more general numerical number representation is 'floating point' or 'float'::

    >>> type(1.7)
    float

The same numerical operators can be applied to floating point numbers as we used for integers. Unless we deliberately want to work with inters, we will probably most often work with floating point representation when describing data, as when we have a measurement of some quantity we would normally want:

    >>> print 3.0/2
    1.5

rather than ``1`` as above. The downsides of floating point representation are:

- the cost of storage is generally higher (more bytes for representation)
- the representation is not always exact, as the data type has a limited number of bits to `store the representation in <http://steve.hollasch.net/cgindex/coding/ieeefloat.html>`_. 

This latter point can lead to unexpected behaviour for coding newbies::

    >>> x = 1e10
    >>> y = 1e-20
    >>> x + y
    10000000000.0

so we have 'lost' the `1e-20` (`1.0 x 10^-20`) here due to the limitations of the number representation. 

Try::

    >>> 1e10 + 1e-5 
    10000000000.00001
    >>> 1e10 + 1e-6
    10000000000.000002
    >>> 1e10 + 1e-7
    10000000000.0

We can include floating point numbers in string formatting with a `%f` symbol. We can expand this by using e.g. `%21.10f` to represent a string conversion of a floating point number with 21 digits (including the decimal point) and 10 decimal places, e.g.::


    >>> '%21.10f'%(1e10 + 1e-6)
    '10000000000.0000019073'

which is not quite the ``10000000000.000001`` that we had in mind. This can cause problems when comparing numbers, so you should generally try to avoid or at least think carefully about the order of operatiopns involving very big and very small numbers. These errors due to representation are called 'rounding errors'. See `docs.python.org <http://docs.python.org/tutorial/floatingpoint.html>`_ for more information on this.

Exercise
~~~~~~~~

Write some lines of code to divide two numbers as floating point numbers, giving an error message if you divide by zero.

You will need to use an ``if`` statement for this, which has the following syntactic pattern (i.e. it will look something like this ...)::

    >>> if this == 10:
    ...    print 'this is ten'
    ... elif this == 11:
    ...    print 'this is eleven'
    ... else:
    ...    print 'this is neither ten nor eleven'


.. _dict:

Dictionaries
------------

Another important data type is the dictionary (dict) class. This is actually core to much of Python. It is in some ways similar to a list, but its elements are stored in arbitrary order and are accessed via 'keys'. An example is::

    >>> x = 100
    >>> this = {'foo':'bar','x':x,1:'hello'}
    >>> print this
    {'x': 100, 'foo': 'bar', 1: 'hello'}
    >>> print this[1]
    hello
    >>> print this['x']
    100

As we can see, if we print all of ``this`` it can be in an arbitrary order. We can also see that the keys can be of different data types (integers and strings so far here) as can the values associated with each key. 

We can add new elements::

    >>> this[1.1] = 'a float'
    
where we add a key which is a float type here (the keys can be any `hashable <http://docs.python.org/glossary.html>`_ type).

We can have a hierarchy of dictionaries, e.g.::

    >>> that = {'first':1,'second':2}
    >>> this['sub'] = that
    >>> print this['sub']['first']
    1

We can combine dictionaries with ``update()``::

    >>> other = {'third':3, 'fourth':4}
    >>> that.update(other)
    >>> print that
    {'second': 2, 'third': 3, 'fourth': 4, 'first': 1}

It is instructive at this point to have a look at ``this['sub']`` which we earlier loaded with ``that``::

    >>> print this['sub']
    {'second': 2, 'third': 3, 'fourth': 4, 'first': 1}

So we note that since we have updated ``that``, the sub-dictionary in ``this`` is also updated. This is because Python does not automatically make a copy ``that`` when we set it in the dictionary, it just makes reference to the existing dictionary. If we wanted to make sure that ``this['sub']`` was not updated when we change ``that``, we should have set ``this['sub']`` to a copy of ``this['sub']``::

    >>> that = {'first':1,'second':2}
    >>> this['sub'] = that.copy()
    >>> that.update(other)
    >>> print that
    {'second': 2, 'third': 3, 'fourth': 4, 'first': 1}
    >>> print this['sub']
    {'second': 2, 'first': 1}

Whether you use a copy or not when you set some value will depend on what behaviour you want. Less memory is used by using a reference only, which can be a big advantage, but the ideas can be a little more complex for beginners.

.. _del:

We can delete an element from a dictionary with::

    >>> del this['sub']['first']
    >>> print this['sub']
    {'second': 2}

noting that we can use ``del`` more widely to delete variables from the name space::

    >>> del that
    >>> print that
    ---------------------------------------------------------------------------
    NameError                                 Traceback (most recent call last)
 
    <ipython console> in <module>()

    NameError: name 'that' is not defined


We can get a list of keys or a list of values::

    >>> that = {'first':1,'second':2}
    >>> that.keys()
    ['second', 'first']
    >>> that.values()
    [2, 1]

We can create dictionaries by zipping together two sequences::

    >>> modisBandRange = ['630-690','780-900','450-520','530-610','1230-1250','1550-1750','2090-2350']
    >>> bandNumbers = range(1,1+len(modisBands))
    >>> modis = dict(zip(bandNumbers,modisBandRange))
    >>> print modis[1]
    
If we then iterate over the dictionary keys::

    >>> for i in modis.iterkeys():
    ...    print i,modis[i]
    1 630-690
    2 780-900
    3 450-520
    4 530-610
    5 1230-1250
    6 1550-1750
    7 2090-2350
 
though you must be careful with dictionaries, since the they are not guaranteed to be stored in any pareticular order. If you want to make sure that you go over keys in order, then you should first sort the keys::

    >>> for i in sorted(modis.iterkeys()):
    ...    print i,modis[i]
    1 630-690
    2 780-900
    3 450-520
    4 530-610
    5 1230-1250
    6 1550-1750
    7 2090-2350


Dictionaries are very useful for a large number of things in Python, but it will suffice to have introduced them here for now.
See ``help(dict)`` for more details on methods for dictionaries. There are useful for a wide range of operations.

Exercise
~~~~~~~~

Create a file containing two columns of data, and call the file e.g. food.dat::

    monkey 	peanuts
    elephant	buns
    dog		bone
    cat		catfood
    
    etc ...

Obviously, **don't** type ``etc ...`` in here ...

Then write some code to:

* read the contents of a file and set up a dictionary with animal names as keys.
* use this dictionary to develop an interactive code that tells the user what food a particular animal eats.


File handling
===============

.. _files:

File input and output
---------------------

One common thing we want to do in programming is to read from or write to files in `ASCII <http://en.wikipedia.org/wiki/ASCII>`_ format. This is simple to do in a high level language such as Python. First, let's generate a dataset that we want to write out::

    >>> data = [[1.,2.,3.,4.,5.],[1.,4.,9.,16.,25.]]
    >>> print data
    [[1.0, 2.0, 3.0, 4.0, 5.0], [1.0, 4.0, 9.0, 16.0, 25.0]]
    >>> print len(data)
    2
    >>> print len(data[0])
    5

This is a slightly different list to the ones we've seen above. It is a 2-dimensional array that we have created by nesting lists. We also see the ``len()`` method which reports the length of a list (or similar data types) in its outer dimension (2 here). ``data[0]`` then is of length 5.

    >>> outfile = file('tmp.dat',"w")
    >>> for i in range(len(data[0])):
    ...     outfile.writelines('%f %f\n'%(data[0][i],data[1][i]))
    ...
    >>> outfile.close()

The file we have created, ``tmp.dat`` should contain::

    1.000000 1.000000
    2.000000 4.000000
    3.000000 9.000000
    4.000000 16.000000
    5.000000 25.000000

We have introduced a few new concepts here. First, we notice how we can open a file *for writing*: ``outfile = file('tmp.dat',"w")``. The variable ``outfile`` is set to the information we get from calling the ``file()`` method (see ``help(file)``). 

.. _range:

Second, we have made use of a ``for`` loop to iterate over the elements in the variable ``data``. 

The method ``range(len(data[0]))`` returns the list ``[0, 1, 2, 3, 4]``, so we could have written::

    >>> for i in [0, 1, 2, 3, 4]:
    ...    outfile.writelines('%f %f\n'%(data[0][i],data[1][i]))

.. _xrange:

In fact, for looping of this sort, we would normally use ``xrange``, an iterable object that doesn't have to explicitly form the list::

    >>> for i in xrange(len(data[0])):
    ...     outfile.writelines('%f %f\n'%(data[0][i],data[1][i]))

Thinking about the list produced by ``range`` is however easier to start with. What happens in the ``for`` loop then is that the variable ``i`` takes the value of each item in the list, sequentially, so the first time we are in the loop, ``i = 0``, and we are writing the elements of the list ``data``, ``data[0][0]`` and ``data[1][0]``.

The ``\n`` character in the format statement is new to us as well. This stands for 'newline', so that after ``data[0][0]`` and ``data[1][0]`` are written as string representations of their floating point numbers, a 'newline' character is written to the file.

The line ``outfile.close()`` closes the file, flushing any data in buffers whilst doing so.

One important feature of this snippet of code is that it shows how in Python, indentation (4 spaces here) must be used to define elements within any iteration / control structure.

Let us now consider how to read data from such a file. This is similar to above::

    >>> indata = open('tmp.dat','r').readlines()

but we can read all data at the same time with the ``file`` method ``readlines()``. We could have done this in more steps as::

    >>> infile = open('tmp.dat','r')
    >>> indata = infile.readlines()

If we now look at what has been read in, we will see::

    >>> print infile
    ['1.000000 1.000000\n', '2.000000 4.000000\n', '3.000000 9.000000\n', '4.000000 16.000000\n', '5.000000 25.000000\n']
    >>> print len(infile)
    5

The list ``infile`` then has 5 elements, the first of which is ``'1.000000 1.000000\n'``. Note that it has a newline character in the end and that it is a string. File input and output of this sort all takes place as strings.

We can split this up into a list 5 x 2 elements using e.g.::

    >>> indata = open('tmp.dat','r').readlines()
    >>> data = []
    >>> for i in xrange(len(indata)):
    ...     data.append(indata[i].split())

This is quite instructive. We know how many elements there are in the dataset from the number of lines we read from the file (``len(indata)``) and we can just loop over these, split the string we have for each line, then append it to the list (noting that we set the original list to ``[]``, and empty list).

But the data would still be strings::

    >>> print data
    [['1.000000', '1.000000'],
     ['2.000000', '4.000000'],
     ['3.000000', '9.000000'],
     ['4.000000', '16.000000'],
     ['5.000000', '25.000000']]

which is probably not what we want, and is in any case the 'wrong way around' compared to our original data representation. 

At the heart of what we need, is to convert a string data type to a float. We do this with the method ``float()``.

    >>> data = []
    >>> values = []
    >>> for i in xrange(len(indata)):
    ...     linedata = indata[i].split()
    ...     data.append(float(linedata[0]))
    ...     values.append(float(linedata[1]))
    ...
    >>> data = [data,values]
    >>> print data
    [[1.0, 2.0, 3.0, 4.0, 5.0], [1.0, 4.0, 9.0, 16.0, 25.0]]

This is more what we are after, although the code we have written is not very flexible (it will only work if there are 2 columsn of data).


Summary
-------

In this session, we have been introduced to some basic concepts in Python. These are mainly associated with some basic operations on the inbuilt Python data types, but we have also come across control using a ``for`` loop and the fact that Python code is indented in such cases. 

  [`boolean`_] [`dict`_] [`files`_] [`float`_] [`for`_] [`integer`_] [`ipython`_] [`lists`_] [`modulo`_] [`print`_] [`range`_] [`strings`_] [`type`_] [`variables`_] [`xrange`_]


Some hints/answers for the exercises
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Strings**

You were asked to modify the following code so that it replaces every time you type 'windows' with 'unix':

.. literalInclude:: python/ex1.py

This can be achieved by:

.. literalInclude:: python/ex1a.py


A second exercise was to try to make your code work with different capitalisation (e.g. Windows -> Unix, windows -> Unix). One way to do that would be::

    >>> print line.lower().replace('windows','Unix')

but that actually does more than is asked for (it will e.g. translate ``WiNdOwS`` to ``Unix``).

More careful control might be achieved through being explicit about the changes required::

   >>> print line.replace('windows','Unix').replace('Windows','Unix') 

A more general solution might be achieved with a dictionary (once you have learned to use them), e.g.:

.. literalInclude:: python/ex1b.py


**Boolean**


You were asked to work out what::

    >>>  (s == 'star' and 'bat') or s

does. The hint supplied was that ``s == 'star'`` is an equivalence test, so it returns ``True`` if the variable ``s`` is set to the string ``star``. In that case we would have::

    >>> (True and 'bat') or 'star'

The result of combining a boolean with a string gives e.g.::

    >>> True and 'any string'
    'any string'
    >>> False and 'any string'
    False
    >>> True or 'any string'
    True
    >>> False or 'any string'
    'any string'

So::

    >>> (True and 'bat')
    'bat'
    >>> 'bat' or 'star'
    'bat'

So, if ``s`` is set to ``star``, then ``bat`` is always returned. If ``s`` is not ``star`` then::

    >>> s = 'not star'
    >>> (False and 'bat')
    False
    >>> False or 'not star'
    'not star'

So, if ``s`` is *not* ``star`` then the value of ``s`` is returned. In effect this replaces ``'star'`` with ``'bat'``.

.. _a single string:

**Lists**

You were asked join together the elements of a list intop s string. The easiest way to do this is::

    >>> print ' '.join(nlist)


or, if some of the elements might not be strings::

    >>> print ' '.join([str(s) for s in nlist])


The statement ``print ' '.join(list)`` looks quite complex, but at heart it is using the string method ``join()`` on the string ``' '``, which is really just the opposite of the string ``split()`` operation we saw above. It happens to be a convenient way to produce a string from a list of strings (provided they all *are* strings).


**Integers**

You were asked to write some lines of code that converts an integer in base 10 to a representation in another base (e.g. 2).

Clearly this needs a loop structure of some sort, as we do not know beforehand how many digits to use, a ``while`` condition would seem appropriate::

    >>> base = 2
    >>> numberBase10 = 3654
    >>> numberList = []
    >>> while numberBase10 > 0:
    ...    numberList.append([numberBase10%base])
    ...    numberBase10 = numberBase10/base
    >>> numberList.reverse()
    >>> print numberList
    [[1], [1], [1], [0], [0], [1], [0], [0], [0], [1], [1], [0]]

The key parts of the algorithm are::

    >>> remainder = numberBase10%base

The modulo operator ``%`` will the remainder, e.g.::

    >>> 10%3
    1
    >>> 3%2
    1

Then, we reduce the current value of the number by a factor of ``base`` in the loop to step on a digit. It is worthwhile trying a 'dry run' for testing something quite simple like this. You can do this on paper, and work out the result you want at each state for a number of cases. We can then run it on the computer and compare outputs. An example might be:

.. literalInclude:: python/ex2.py

resulting in::

    3654 = N x 2 r 0
    1827 = N x 2 r 1
    913 = N x 2 r 1
    456 = N x 2 r 0
    228 = N x 2 r 0
    114 = N x 2 r 0
    57 = N x 2 r 1
    28 = N x 2 r 0
    14 = N x 2 r 0
    7 = N x 2 r 1
    3 = N x 2 r 1
    1 = N x 2 r 1
    [[1], [1], [1], [0], [0], [1], [0], [0], [0], [1], [1], [0]]


**Floating point**

You were asked to write some lines of code to divide two numbers as floating point numbers, giving an error message if you divide by zero. You were given a hint to use an ``if`` statement and shown the syntax.

Possibly the simplest way to achieve this then is::

    >>> numerator = 10
    >>> demoninator = 3
    >>> error = False
    >>> if demoninator != 0:
    ...    result = float(numerator)/float(demoninator)
    ... else:
    ...    print 'Warning ... divide by zero'
    ...    result = 0.0
    ...    error = True
    >>> print result,error


Another way would be to use an assert statement::

    >>> numerator = 10
    >>> demoninator = 3
    >>> error = False
    >>> try:
    ...     assert(demoninator != 0)
    ... except AssertionError:
    ...     print 'Warning ... divide by zero'
    ...     error = True
    ...     result = 0.0
    >>> print result,error

which has the same effect, but uses a different mechanism to get there.
See ``help('assert')`` or `other notes on using assert effectively <http://wiki.python.org/moin/UsingAssertionsEffectively>`_ . 

**Dictionaries**

You were asked to write some code to: 
 
* read the contents of a file and set up a dictionary with animal names as keys.
* use this dictionary to develop an interactive code that tells the user what food a particular animal eats.

The file contained 2 columns, representing animal names and food names.

We can base this code on the **strings** example code above:

.. literalInclude:: python/ex1b.py

All we really need to do is to replace where we set up the dictionary with some code to read it from a file.

We can use the code above for files for doing this, e.g.:

.. literalInclude:: python/animal1.py

which works quite well, except when it doesn't have an entry. Its a good idea to foresee this sort of issue and trap it, e.g.:

.. literalInclude:: python/animal2.py

or, alternatively, using ``try``:

.. literalInclude:: python/animal3.py

A slighly better version might be:

.. literalInclude:: python/animal.py

There is lots to customise in a code like this, and many ways of doing things. The key is to make sure you have the behaviour you want and that it is robust to unexpected inputs.


Writing and Debugging Python Code 
=================================

In the previous session, we typed Python commands at a prompt, i.e. we used Python interactively. We will now mostly be developing Python codes that we can re-use, so we will need to save them in a file. You can do this using your favourite texteditor (such as vi ;-)) or development environments such as `IDLE <http://docs.python.org/library/idle.html>`_ or `many others <http://wiki.python.org/moin/IntegratedDevelopmentEnvironments>`_. If you are working on your own computer, have a look around at the different environments available and what people say about them, and choose one to use. Given the intensity of this course however, we will assume only a basic setup here, running your python code from a shell prompt in Unix and some editor for creating and editing files.

It is useful to have access to a debugger when writing code. This allows you more easily track down problems that you have, but it is bad practice to develop the code in a debugger environment. As part of this coding, we will show you how to make use of a debugger to help track down problems.

In this session
---------------

We will introduce the following new topics:

    [`import`_] [Unix: `ln`_] [`pdb`_]

we will also come across the following:

    [`locals`_]

Writing and Debugging Python code
---------------------------------

.. _ln:

First, lets set up a useful directory structure in your Unix environment. Type the following at the Unix prompt::

    berlin% cd ~
    berlin% mkdir -p DATA/src/python
    berlin% ln -s ~/DATA/src ~/src
    berlin% ln -s ~/DATA/bin ~/bin
    berlin% cd src/python

This will create a ``src`` ('source') directory in your ``DATA`` area, with a subdirectory ``python``. The command ``ln -s ~/DATA/src ~/src`` makes a *symbolic link* from ``~/src`` to ``~/DATA/src`` so that it will seem to you (and other users) that your ``src`` directory is in your home, rather than on the data disk (where it actually is).

Let's start with a simple piece of Python code, but first create a new directory to keep it in::

    berlin% mkdir ~/src/python/hello
    berlin% cd  ~/src/python/hello 

The Python code, that we want to be in the directory ``~/src/python/hello`` (i.e. ``~/src/python/hello/helloWorld.py``) is:

.. literalInclude:: python/helloWorld.py


Once you have created *and saved* the file, you can make it executable, and then run it as if it were any other Unix command::

    berlin% chmod +x ~/src/python/hello/helloWorld.py
    berlin% ~/src/python/hello/helloWorld.py

This should produce::

    hello world

and this will be for many of you your first computer program. 

You might check the file permissions once you have used ``chmod``, just to check that what has happened is what you expected (hint, in case you have forgotten, use ``ls -l filename``).

Another way to 'run' this program are::

    berlin% python ~/src/python/hello/helloWorld.py

and in fact, `this is what the first line of your program effectively does <http://en.wikipedia.org/wiki/Shebang_%28Unix%29>`_:

.. literalInclude:: python/helloWorld.py
    :lines: 1-1

By including this line, and making the file executable however, we do not need to explicitly run it with python at the command line. You should generally include this first 'hash bang' line in your Python codes.
One other thing to note, if you look in the directory your code is, you should see a file ``helloWorld.pyc`` which is the compiled version of the code (this is automatically done). It should run slightly faster then if you run it again, as it no longer has to compile.

Next, we will show a simple example where you might use a debugger (``pdb``). Create the file ``helloBroken.py``:

.. literalInclude:: python/helloBroken.py

If you run this, you will probably get the message::

    Traceback (most recent call last):
      File "src/python/hello/helloBroken.py", line 6
        print 'hello %s, did't you know that %d + %d = %d?'%(who,one,one+one)
                            ^

Once you are used to spotting bugs (and you *will* make mistakes and create bugs), the meaning of this should be quite obvious, but for newbies at coding it can look quite complicated. One important thing to remember about tracking down and fixing bugs is to do them in order: if you fix a bug early in the code, it may make some apparent bugs later on go away. Here, we are lucky in that there is apparently only one bug. This should be easy to spot and fix. We know it is on line 6 of the code
and the little arrow is giving us a good clue to what the problem is. 

Fix this bug **without looking at the next stage below** (only this one, in case you think you have spotted others!) and try to run again:

.. literalInclude:: python/helloBroken2.py

We fixed the issue with the quote (We did it here by using ``"`` to encapsulate the string, but you might have just as readilly removed the offending ``'``), but now there is another bug. One thing to learn from this is, especially when you start coding, is to only write small sections of code, **then to test them**. Working out *how* to test a piece of code is a skill that will develop over time. 

The bug now then is quite a simple one::

    Traceback (most recent call last):
      File "src/python/helloBroken.py", line 6, in <module>
        print "hello %s, did't you know that %d + %d = %d?"%(who,one,one+one)
    NameError: name 'who' is not defined

.. _pdb:

It's clearly still on line 6, and it concerns the variable ``who``. We might just be able to look at the code and spot what the problem here is, but sometimes it is more difficult to see. This might be a case to invoke a debugger. The question we want to ask is 'why isn't this variable I want to use ``who`` defined?`. We can do this by importing and using the debugger package:

.. literalInclude:: python/helloBroken3.py

.. _import:

The line:

.. literalInclude:: python/helloBroken3.py
    :lines: 2-2

imports the ``pdb`` package, then we refer to a method set_trace() in this package by:

.. literalInclude:: python/helloBroken3.py
    :lines: 7-7

We have places the 'trace point' just before where we know the bug is, so that we can investigate what is going on. Now when we run, we get a ``(pdb)`` prompt::

    > /home/plewis/src/python/helloBroken.py(8)<module>()
    -> print "hello %s, did't you know that %d + %d = %d?"%(who,one,one+one)
    (Pbd) 

We can now run various commands within ``pdb`` to try to work out the problem. Typical ones are: 

- ``b`` : set a breakpoint
- ``c`` : continue (to next breakpoint)
- ``n`` : next line
- ``s`` : step (into module)
- ``p`` : print (e.g. ``p who``)
- ``u`` : up (one level)
- ``d`` : down (one level)
- ``l`` : list (or ``l 1`` to list lines atrting at 1)
- ``?`` : help
- ``h`` : help

In this case, we might try::

    (Pbd) p who
    *** NameError: NameError("name 'who' is not defined",)

but that doesn't actually take us much further than the original error message:: ``who`` is simply not defined. So, we need to see why. It would be useful to list the code at this point::

    (Pdb) l 1
      1  	#!/usr/bin/env python
      2  	import pdb
      3  	
      4  	whom = 'world'
      5  	one = 1
      6  	
      7  	pdb.set_trace()
      8  ->	print "hello %s, did't you know that %d + %d = %d?"%(who,one,one+one)
    [EOF]
    (Pbd) 

.. _locals:

from which is *should* be obvious, but we still might not see it. From ``pdb`` we can type and run any Python commands to help us. In this case, we might find `locals() <http://docs.python.org/library/functions.html#locals>`_  quite helpful::
  
    (Pdb) locals().keys()
    ['one', '__builtins__', '__file__', '__doc__', 'whom', '__name__', '__package__', 'pdb']

``locals`` returns a dictionary of local variables that *are* defined, and ``locals().keys()`` tells us the 'names' (the 'keys') of these variables. We see a number of terms starting and ending with ``__`` (e.g. ``'__doc__'``) that we do not need to be concerned with yet, but we also see that the only other variables defined are: ``'one'``, ``'whom'`` and ``'pdb'``. It should be clear to us know that we have mistakenly assigned the variable ``whom`` when we meant ``who`` (or *vice-versa*, if you like). You can quit the debugger now and edit the file. The problem happened on line 4 of the code, and is easy to fix:

.. literalInclude:: python/helloBroken4.py

If we leave the trace point in, we again stop at line 8 of the code. We could step over that line with::

    (Pbd) n
    TypeError: 'not enough arguments for format string'

but we see one more error: ``'not enough arguments for format string'``. That should quite easy to spot and fix. If you think you know the correct line here, you can try it out at the debugger::

    (Pbd) print "hello %s, did't you know that %d + %d = %d?"%(who,one,one,one+one)
    hello world, did't you know that 1 + 1 = 2?

so we can now go back and fix that line in the code file, and run the whole thing (finally).

The errors here should not have been hard to track down, but they can be in a large piece of code, and sometimes the errors can be quite subtle. There is definitely a skill to coding, and you will (hopefully) get better with practice, but for the moment, just try to remember to:

- plan the code before you start writing, breaking some big 'problem' down into small achievable chunks
- make the code as clear and simple as you can, using appropriate library functions rather than continuously re-inventing the wheel
- write it in small increments, and keep testing the code.

Summary
-------

In this session, we have introduced the concept of writing Python code in a file, rather than interactively, and shown some ideas on how to track down problems in the code you develop (debugging).

We have covered the following new topics:


    [`import`_] [Unix: `ln`_] [`pdb`_] 

we have also come across the following:

    [`locals`_]

