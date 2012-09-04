Some help information for setting up and using Python
=====================================================

Where to get Python
-------------------
We have several Python distributions on the Geography Unix machines, including an `EPD distribution <http://www.enthought.com/products/edudownload.php>`_ that you can very easily download and install on your own computer, if you have one. Most operatng systems will in any case come with a Python distribution, and you can most likely make direct use of this without using EPD. In any case, you can have multiple python distributions on the same computer if you wish.


Getting new Packages
--------------------

For most Python distributions, you will be able to use `easy_install <http://pypi.python.org/pypi/setuptools>`_ to easily install (!) new packages and update your distribution. For the earlier sessions in this course, the only packages that you need (that are normally included with basic Python distributions) are numpy, matplotlib, and scipy. One convenient way to use python is through `ipython <http://ipython.org/>`_. To check that you have access to this, open a Unix shell (or other interfaces on non Unix machines) and type::

    berlin% which ipython
    /opt/epd-7.1-2-rh5-x86_64/bin/ipython

If the response is::

    berlin% which ipython
    ipython: Command not found.

then either it is not installed on your computer or it is not in your *path*. On the UCL Geography machines, it is probably in ``/opt/epd-7.1-2-rh5-x86_64/bin/ipython``_. If you are working on this system, check that this file exists (``ls -l /opt/epd-7.1-2-rh5-x86_64/bin/ipython``). You *can* just type::

    berlin% /opt/epd-7.1-2-rh5-x86_64/bin/ipython

to start your interactive Python session in this case, but it is probably better to put this in your path. To do that (and *only* if ``which ipython`` returned ``Command not found``) edit the file ``~/.cshrc`` (if you are using ``tcsh`` as your shell, or e.g. ``~/.bashrc`` if you are using ``bash``) and toweards the end of the file, include the following lines::

    set path = ($path /opt/epd-7.1-2-rh5-x86_64/bin)

If you are using ``bash`` or another shell, include the appropriate commands to set the shell variable ``path`` (and/or the environment variable ``PATH``). In the shell, then type (for ``tcsh``)::

    berlin% source ~/.cshrc

to update your path. Typing ``which ipython`` should now give the result we want. 

If you don't have ``ipython`` on your system, but you do have ``easy_install`` (check with ``which easy_install``, it will nortrmally be in the same place that ``ipython`` would be) you can use this to install ``ipython``. You will normally do this as ``root`` (the super user, or administrator) if you are using your own computer. On the Geography system, you have to ask Chris Knell if you need any new software, though you will find that you can install packages locally (i.e. just for yourself) if you really need them and noone else is likely to do so. If you have your own linux or OS X computer and you need to install ``ipython`` type::

    home% sudo easy_install ipython

which will prompt you for the root (system/ administrator) password and then install the package. This is the same for any other package you need, so to check you have appropriate ``numpy``, ``matplotlib`` and ``scipy``::

     home% sudo easy_install numpy matplotlib scipy


