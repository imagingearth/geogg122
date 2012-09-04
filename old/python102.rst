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

