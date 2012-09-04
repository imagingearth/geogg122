============================
A Brief Introduction to Unix
============================

This course will be taught mainly under a Unix operating system. This part of the introduction is intended for background reading and we will not go through it in quite the same way in class. 

Unix commands and and a few options learned here:

 [`alias`_] [`cd`_] [`chmod`_] [`cp`_] [`df`_] [`ls`_] [`mkdir`_] [`mv`_] [`pwd`_] [`quota`_] [`rm`_] [`rmdir`_]

with a few options:

  [`cp-R`_] [`ls-l`_] [`rm-f`_] [`rm-i`_] [`rm-r`_]

The Unix symbols come across are:

 [``/``: `slash`_] [``\``: `backslash`_] [dotdot: `..`_] [dot: `.`_] [tilde/twiddle: `~`_] [star/wildcard: `*`_] [single wildcard: `?`_]


We will cover this material in week 1 of the class. You will need to have become familiar with the basic concepts and commands to progress through week 2 and beyond.

What is Unix?
=============
UNIX is a multi-user operating system: that is, a suite of programs which run on a computer and allows interface to the hardware and software available. It allows many users to share a powerful machine and all the available resources, each user running their own processes simultaneously. This true multi-tasking aspect of UNIX allows a far greater flexibility than is possible with other operating systems, even more recent multi-tasking versions of popular PC operating systems (note that the `linux <http://en.wikipedia.org/wiki/Linux>`_ is simply a 'flavour' of UNIX & that the Mac operating system `OS-X <http://en.wikipedia.org/wiki/Mac_OS_X>`_ has a good deal of UNIX system within it). The advantages of a truly flexible multi-tasking operating system has been demonstrated with the popularity of UNIX in the scientific, engineering and financial communities, along with the rise of Linux and OS-X.

`X11 <http://en.wikipedia.org/wiki/X11>`_ is the windowing system that you will generally use to interface with the operating system. A key aspect of this has always been the idea of remote graphical user interfaces via X11, which allows a user to run and visualise processes on different Unix machines. You are not limited to accessing the computer you are sat in front of, but can easily make wider use of local or external resources. You will find this useful as you can log on to the UCL Geography Unix computers from outside UCL (from pretty well any other operating system) and (with appropriate X11 software such as `cygwin <http://en.wikipedia.org/wiki/Cygwin/X>`_ or `exceed <http://connectivity.opentext.com/products/exceed-freedom.aspx>`_, if you are working from a Windows computer, or directly from any Unix/linux computer os OS-X machine) run windowing sessions the same as if you were physically at the UCL computer (given sufficient bandwidth). 


Workstations and networks
-------------------------

Workstations that run UNIX are not like the way most people use PCs running Windows... At any time of the day or night a UNIX machine is running literally hundreds of processes simultaneously: Some are long-term user processes (such as research experiments) placed at low priority to avoid affecting other users, which may run for weeks, but most are concerned with the second by second activities of maintaining the network.

Physically, the network consists of wires (ethernet cables, phone lines, fibre-optic cables etc.) or wireless connections (locally and externally) running between computers both at local and remote sites. At the local level (within a University Dept. for example) the wires literally connect every machine to every other, either in a loop, or in a star-like arrangement with machines linked around central communications hubs. Such arrangements of connections, machines and attached peripheral devices is known as a Local Area Network or LAN. Larger arrangements of connections, for instance between departments in a university rather than individual computers, are known as Wide Area Networks or WANs.

It is through this ability to transparently network computers together that UNIX really gains its power. Very often the data a user processes on one computer is actually stored on another (a paradigm that has (indirectly) led to the development of the Internet and World Wide Web). Similarly it is commonplace to process data on one machine whilst physically sitting in quite a different location (even on a different continent!). The limiting idea of the machine that you are sitting in front of being the machine you are using for processing (as in the PC-based computing environment) is very much obsolete in the case of UNIX computing. Using the network, it is also possible to break large processes into a number of smaller jobs and distribute them across multiple machines simultaneously, thereby reducing execution times dramatically. In a properly set-up UNIX LAN network, the storage of a users data on a remote machine, or their working on a remote machine should be a relatively transparent operation. Such concepts of networking are not confined to UNIX machines, although UNIX (in all its varieties) is far and away the most common from of operating system used for wide area networking.

Because a UNIX machine never stops processing, the are never switched off by anyone other than the system manager or a relevant member of staff. Simply switching off as you might with a PC can cause irreparable damage to a UNIX machine and/or the data stored on it - remember, your data/project could be on the disk you just killed, so don't do it! If you think that there is something wrong with a machine, do not attempt to fix it yourself: call or email the system manager or ask a knowledgeable person for advice. Under no circumstances should you attempt to reboot a workstation yourself, as unless shut down properly damage to data, both yours and that of others is likely to result.

Many workstations you will come across have a simple power-saving device: the screen turns itself off if the keyboard hasn't been used for a few minutes. To turn the screen back on, simply press a key on the keyboard such as shift, ctrl or the space bar. Often the monitor will have been turned off by the last user to save power (and to stop the lab heating up!) - in most cases, the monitors have a switch or button located on the lower right front of the monitor. If the monitor is on, a small green LED will light up. This is the only switch you should ever touch on the workstations. If it's not on the front of the monitor, please leave it alone. 

Accounts and passwords 
----------------------
Since UNIX allows many users access to the same computer at the same time, there has to be some way of separating each users data, processes and storage space. This is accomplished by means of accounts, created for each user by the system manager. Each person maintains their data and programs within their own account, and their processes are identified when running by means of their account name. Usually an account name will be a construct of the user's real name, but not always. This account name is also known as your username (e.g. Lewis's username is plewis). As an aside, if you have already registered with ISD you will have been issued a username from the ISD system of the form ucfaxxx, which is a separate account from your Geography one. The account name for studxents will be the same on the UCL Geography system as it is on the wider UCL system, but the computers you access (and you password) will generally be different.

To provide protection for users' data and processes, each account is assigned a password. This password will be given to you by the system manager, but you may change it at any time. You must keep this password secret, and should never allow other people to use your account. Other people can make mistakes and damage your data - and even if it was your best friend it will be your responsibility (letting other people use your account is an infringement of college regulations, and could result in a suspension of your computing privileges, or worse). Passwords are stored in encrypted form on the network so that not even the system manager can access them. As a general rule passwords should be changed every couple of months or so, but there are rules for choosing them: you must not use your username, your real name or any derivative (including backwards etc.), anybody else's name, birthdate, favourite colour, football team, pet, or any word in any dictionary of any language - these are all too easy to break/guess. As are characters from film, Tv etc. If you know it - someone else does too. Passwords must be a minimum of 6 characters long, preferably 8, and should contain a mix of letters, numbers (both upper and lower case - to UNIX, an ``a`` and an ``A`` are not the same) or punctuation such as commas of exclamation marks. Try not to use combinations of keys involving the ctrl key, as this can lead to difficulties when trying to log in. Only the first 8 characters of the password are significant. 

Logging in
----------
The process of signing on to the computer is known as the login process. Sometimes people will refer to your account as your login. This is because when the computer is waiting for somebody to use it displays a login prompt. There are various interfaces to logging in, but they will all in some way provide a text space for you to type your username (e.g. ucfxabcd). Generally, you hit 'return' (the return or enter key) or sometimes click on a 'continue' button (or similar) and then enter your password. The password will not generally be shown (it may not show anything or may show ``********``). In the Geography Unix lab, you have a selection of windowing systems (that run on top of the basic X11 setup but all of which use X11) and you are free to choose whichever you want. For teaching classes however, its generally best that we all use the same one. 

When successfully logged in, if you are sitting at a workstation then you will usually have several areas to type in, or windows, started up for you along with such graphical utilities as a clock and a calendar.

The command line
----------------
The UNIX prompt is a sequence of characters that the part of the operating system (OS) that you interact with, known as the shell, places at the start of each line when it is expecting you to enter a command. Often this prompt will be formed by the name of the machine to which you are logged in, followed by a ``%`` sign. For instance::

    berlin%

which will indicate that you are logged on through a window (which you might call a terminal or a shell though these are subtly different things).

The nature of the prompt will vary from system to system, but the Geography machines have a prompt as above. When you become experienced you can customise the prompt to your own liking. The cursor (a small solid rectangle or underscore symbol) placed after the prompt tells you where your current typing position is (clicking in the window with the mouse doesn't mover the cursor - it always remians at the end of the current line you're on). The current line with the prompt is therefore known as the command line. Depending on the particular shell you are using and the sort of keyboard you have, you may be able to use up and down arrows to quickly go back through commands that you have typed at that prompt (in that shell session) (i.e. your history).

Logging out
-----------
When you have finished your session at the computer, you must log off. To achieve this from a remote PC/Mac connection, simply type logout or exit at the prompt. From within a windowing session at the machine itself, select the logout option from your root menu (see the section on the windowing system for more details), and then confirm the logout by clicking on yes. If you leave yourself logged on then other people may come along and use your account, access your email etc. Whilst in a University environment this is not necessarily a problem - the next user will probably come along and log you out so that they can log on themselves it is important to log out so that other people don't waste time wondering whether you have finished, or have just popped out for a few minutes. Don't lock your workstation - this is anti-social behaviour as it prevents anyone else using it, and if we see it we'll log you out anyway, and probably take all your pocket money away. If you leave for more than a few minutes, log yourself out. One of the advantages of a UNIX system is that you can leave a job running in the 'background' (don't worry, we'll get to that later) which means it'll keep running for as long as you want even after you log out. 

The UNIX file system
====================
All information in UNIX, whether it is a program, data or text, is stored in files. These files are maintained by the operating system on hard disks (usually), and read into the computer's memory when required. Files may be grouped together in directories (equivalent to folders), and these directories may themselves contain other directories and/or files. In fact, directories are really a special kind of file, but the user perceives the whole structure as forming a hierarchy of files and directories. This hierarchy is known as the filesystem. When UNIX computers are networked, the filesystem is not contained within one single machine, but spans the entire network. Each file and directory within the network filesystem is addressable via its own unique name - its filename, or directory name, and to the user the fact that the filesystem straddles multiple machines and hard disks goes largely unnoticed.

.. _slash:

The filesystem may be visualised as the roots of a tree. At the very top level of the filesystem on each individual machine resides the root directory, denoted ``/`` (slash). 

Beneath this directory lie the other directories containing files and further directories, including data and references to data stored elsewhere on the network. 

Absolute and relative path names
--------------------------------

We have already mentioned that every file or directory in the filesystem is uniquely addressable by its filename or directory name. In fact a file's full name is a description of the path from the root of the file system to the file itself. For instance, the directory ``bin`` under the ``usr`` directory has the full name:

    ``/usr/bin``

Note that as well as being the root of the filesystem, ``/`` is also used as a directory separator for full filenames and paths (note that is the opposite of the Windows/DOS directory separator ``\``). Here the directory bin
is reached by starting at the root of the system, ``/``, going into the ``usr`` directory. A directory contained within another directory is known as a sub-directory of its parent, or container, directory. The ``/usr/``
section of the full filename is known as the absolute path(name) to the file - absolute because it starts at the root of the system. With this nomenclature we are able to move around the filesystem.

.. _`..`:

Similarly, relative pathnames are permissible, describing the route to another path or directory from the current directory: the file ``xeyes`` in the directory ``/usr/X11/bin`` may be addressed either absolutely as: 

    ``/usr/X11/bin/xeyes``

or relative to the ``/usr/X11/lib`` directory as:

    ``../bin/xeyes``

where ``..`` is a special symbol meaning 'up one directory level'.
An analogy is the address of your next door neighbour's house. If you wanted to tell a friend what next door's address is, you could give them the house number, the street, the city, the post code, and even the country. That's the absolute path name to your neighbour's house. Of course it's much easier to specify "one house up from mine" or "number 18" etc. This is the relative path (relative to yours).

Negotiating the file system
---------------------------
Each user in a UNIX network system has specific area of the filesystem belonging to them known as their **home directory** in which they are initially placed when they log on. Armed with a basic knowledge of the structure of the filesystem, each user is free to explore and visit almost any area of the system unless it has been specifically protected by its owner.

.. _cd:

To move around the filesystem the `command <http://pubs.opengroup.org/onlinepubs/9699919799/utilities/cd.html>`_ ``cd`` [#]_, for change directory is generally used, for example::

    berlin% cd /

which will (once you hit the return key to execute the command) change your location, your 'working directory' to the root directory ``/``. A few things to pay attention to when first coming across this: 

- first, there is space ('white space' as we call it) between the command ``cd`` and the 'argument' ``/``. This is one or more spaces or tab characters so that the shell can understand that you want to run the command ``cd`` and give it some extra information (where to change directory to in this case), rather than, for example typing ``cd/`` in which case the shell will interpret ``cd/`` as the command you are trying to run; 
- second, if you think about what you want to achieve with the command, (change directory to somewhere) it should be quite apparent that apart from the command, you also need to give the shell an indication of where you want to go (``/`` here) so you (normally) will have to type ``cd somewhere`` where ``somewhere`` is where you want to go. When you are first using these commands, pausing and thinking about what you want to achive is particularly important. Later, it will generally become second nature (as when you learn any new language).

Now, if you type::

    berlin% cd home/plewis

You will change directory to the subdirectory ``plewis`` of the subdirectory ``home`` of ``/``, which is the same as doing (using an absolute pathname)::

    berlin% cd /home/plewis

These *look* similar at first glance, but the second importantly has a ``/`` at the front of the directory name, and so is an **absolute** pathname, whereas the first does not, so it is a **relative** pathname.

The idea should be simple and intuitive once you get the idea of ``/`` being a separator and ``/`` being the top of the directory tree (the root directory). 

You should practice moving around the file system. **Try examples such as moving from your own home directories to that of your neighbour in the class, using relative and absolute filenames.**

.. _pwd:

With all these ``cd`` exercises you might easily lose track of where you are. The command that returns the name of the current working directory (i.e. where you are) is ``pwd`` (print working directory)::

    berlin% cd /home/mdisney/../plewis
    berlin% pwd
    /home/plewis

.. _`~`:

Since your home directory is somewhere you will want to refer to quite often, there is a special symbol ``~`` (the tilde symbol, often called twiddle). So::

    berlin% cd ~

should change directory to your home::

    berlin% cd ~
    berlin% pwd
    /home/plewis

You refer to the home of a particular user with the ``~`` symbol as well, so ``~plewis`` refers to the hom of the user ``plewis``.

**Make use of** ``~`` **to change to the home directory of your neighbour, check where you are with the appropriate command, and confirm that it is what you expected.**

.. _`.`:

Another useful symbol is ``.`` ('dot') which stands for the current directory, so::

    berlin% cd ~plewis/.
    berlin% pwd
    /home/plewis
    berlin% cd .
    berlin% pwd
    /home/plewis

``cd .`` apparently does nothing, but really it just changes directory to be where we are now. This might not seem very useful, but we will find it useful later.

.. _ls:

The next command to introduce is ``ls`` (list) which produces a list of directory contents::

    berlin% cd ~mdisney
    berlin% ls
    DATA	Desktop
    Documents 	Downloads

By default, this will show you all (nearly all) the files and directories where you are now. You can get a listing of another directory (or file) by using that directory (or file) as an argument to the command, e.g.::

    berlin% ls ~plewis/public_html/eoldas/

This is the same ``ls`` command as previously, but we have used a more complex construct for where we want it to provide a listing of. The directories referred to are in the subdirectory ``eoldas`` of the subdirectory ``public_html`` of the home of ``plewis`` (``~plewis``). 


Making and breaking things
==========================

So, we understand the structure of the filesystem, we have come across some of the Unix symbols (``~``, ``.``, ``..``), we can change directory, and we can get a listing of files or directories. That's not far off the minimum set of concepts that you need for using Unix, but we still don't know how to move or copy data around or how to make our own directories. 

.. _mkdir:

To make a directory, you use the command ``mkdir`` and then provide the name of the directory you want to create. You can only make directories (or copy or move files) where you have permission to do so, so we should first ``cd`` to the subdirectory ``DATA`` in your home directory::

    berlin% cd ~/DATA
    berlin% mkdir someStuff

This will make the directory ``~/DATA/someStuff``. Check that that has happened (e.g. list what is in ``~/DATA/``) and then change directory to this new location::

    berlin% cd ~/DATA/someStuff

.. _rmdir:

You can remove an **empty** directory with the command ``rmdir``. 

**Try creating some new directory, check that it is as you expect (with ``ls`` or ``cd`` and ``pwd``), then try deleting it with ``rmdir``. Remember that the directory has to be empty to use this command. There are other ways of deleting directories and their contents that we will come across a little later.**


.. _cp:


The command `for copying a file is <http://en.wikipedia.org/wiki/Cp_unix>`_ ``cp``, e.g.::

    
    berlin% cp ~plewis/msc/hello.dat .

**Check that the file has been correctly copied using an appropriate command**.
Note the 'dot' ``.`` here: we are telling the command ``cp`` to copy the file ``~plewis/msc/hello.dat`` to the current directory ``.``. Note also the whitespace between the command ``cp`` and the two arguments ``~plewis/msc/hello.dat`` and ``.``.
A common mistake people make when first using this command is not giving two (actually, two or more) arguments, but if you think about what information you would need to give to the computer to copy a file from somewhere to somewhere else, you will soon learn that you need at least two arguments.

.. _*:

We can copy more than one file at a time using wildcard characters. The one you are likely to come across most often is ``*`` which stands for 'zero or more characters' in a filename or directory name. To explore this, lets first get a listing of all of the files that end with ``.dat`` in the directory ``~plewis/msc``::

    berlin% ls ~plewis/msc/*.dat
    /home/plewis/msc/atm.dat      /home/plewis/msc/header.dat      /home/plewis/msc/max.dat
    /home/plewis/msc/country.dat  /home/plewis/msc/hello.dat       /home/plewis/msc/points.dat
    /home/plewis/msc/dem.dat      /home/plewis/msc/helloWorld.dat  /home/plewis/msc/popden.dat
    /home/plewis/msc/forest.dat   /home/plewis/msc/landsat.dat
    /home/plewis/msc/head.dat     /home/plewis/msc/listing.dat

.. _?:

Here, we have used the wildcard to specify a set of files that follow a pattern (``*.dat``). We can use another wildcard ``?``
to get more subtle control. This stands for 'one character', so::

    berlin% ls ~plewis/msc/???.dat
    /home/plewis/msc/atm.dat  /home/plewis/msc/dem.dat  /home/plewis/msc/max.dat

refers to files with any three characters, followed by ``.dat``. 

If we wanted all the files that start with ``h`` and end ``.dat`` we could use::

    berlin% ls ~plewis/msc/h*.dat
    /home/plewis/msc/head.dat    /home/plewis/msc/hello.dat
    /home/plewis/msc/header.dat  /home/plewis/msc/helloWorld.dat

To copy multiple files to the same place then, we could simply list the names::

    berlin% cp  ~plewis/msc/hello.dat ~plewis/msc/helloWorld.dat .

**Don't forget the** ``.`` **here, or you be asking it to copy** ``~plewis/msc/hello.dat`` **to** ``~plewis/msc/helloWorld.dat`` **!!**. 

However, you should be able to use wildcards to achieve this more simply. 

**Do that now. Make a new directory called e.g.** ``~/DATA/cpTest`` and copy the files** ``hello.dat`` and ``helloWorld.dat`` **to the new directory, and check that they are there.**

.. _ls-l:

You can generally modify the behaviour of a Unix command by using command line options. The basic style of this is a minus character then a single letter or double minus characters then some word, but this pattern is not always strictly adhered to. A useful option for the command ``ls`` is ``-l`` which gives a long listing (i.e. more details about what it finds). The result will be something of the form::

    berlin% ls -l ~plewis/public_html/eoldas/
    total 652
    drwxrwxr-x 3 plewis plewis  4096 Sep 14 19:28 _images/
    drwxrwxr-x 2 plewis plewis  4096 Sep 14 17:52 _sources/
    drwxrwxr-x 2 plewis plewis  4096 Sep 14 17:52 _static/
    -rw-rw-r-- 1 plewis plewis 26117 Sep 14 17:52 atmos.html
    -rw-rw-r-- 1 plewis plewis 19023 Sep 14 17:52 eoldas_ConfFile.html

This displays information on the owner of a file (``plewis`` here), the size of the file (e.g. ``~plewis/public_html/eoldas/atmos.html is 26117 bytes, which is 25.5 KB), and when it was last modified (``Sep 14 17:52``). The first field that you see (e.g. ``drwxrwxr-x``) is a series of codes that tells you about what type of file it is (``d`` in the first element means that it is a directory) then there are three sets of three elements that may be set to ``rwx`` or unset as in ``---``. These refer to read ``r``, write ``w`` and execute ``x`` permissions for this file, so that if you see e.g. ``rw-`` that means that read and write permission are set but not execute.  Note that directories have the ``x`` bit set if you are to be able to see into that directory, but you will not generally alter that.

**Use** ``ls -l`` **to check that the file sizes of** ``hello.dat`` **and** ``helloWorld.dat`` **are the same as they were in the place you copied them from (**``~plewis/msc``**)**.

The three sets of ``rwx`` bits that you saw when you used ``ls -l`` refer to permissions for different users of the system. The first is for the owner (``plewis`` in this case). The second is for people in the same group as the owner (to enable sharing). The third is for the rest of the world. So, if we saw the file permissions::

    -rwxr-xr-x

this would mean that everyone can read and execute this file (execution means that it is a 'program' that we can 'run'), but only the owner has write permission.

.. _chmod:

An obvious question at this point is 'how do I change file permissions?'. This is generally done with the `the command <http://en.wikipedia.org/wiki/Chmod>`_ ``chmod``. 
This command can be used in a number of ways, one is e.g.::

    berlin% chmod +r hello.dat

to add read permission (similarly for ``+w`` or ``+x``), or ``-r`` etc. to remove read permission. You can do this for specific sets (user, group, others (not in group) and all users) through specifying one or more of ``ugoa``, so::

    berlin% chmod a-r hello.dat

would remove write permission for all users but::

    berlin% chmod u+r hello.dat

would restore it for the user (the owner). 

An alternative mechanism for achieving this is to see the information in ``rwxrwxrwx`` as octal (base 8) bit fields, so if wanted to set the permissions to ``rwxr-xr-x`` this would be 866, or ``rw-r--r--`` would be 644. It is often useful to use ``chmod`` in this way.

.. _rm:

We know how to copy files, so next we need to know how to delete them. This is done with the command ``rm`` (`remove <http://en.wikibooks.org/wiki/Guide_to_Unix/Commands/File_System_Utilities#rm>`_). For example, to remove (delete) the file ``~/DATA/someStuff/hello.dat`` we simply type::

    berlin% rm ~/DATA/someStuff/hello.dat

.. _alias:
.. _rm-i:

*Sometimes* this may ask you for confirmation, i.e. 'do you *really* want to remove this file?') which is something we often put on for new users. This is to stop you accidently removing important files, but when you get used to Unix, you can get rid of that annoyance. When this occurs, what is actually happening is that when you type ``rm`` it is interpreted as ``rm -i``, i.e. we have switched on the ``-i`` option to ``rm`` (which is what causes this checking to be invoked). This is known as *aliasing* whereby a command is translated through an alias. You can get a full list of aliased commands by typing::

    berlin% alias

After you are used to using Unix, you can customise your own aliases. For the moment, we will note that you can *unalias* a command using ``unalias``, e.g.::

    berlin% unalias rm

.. _backslash:

or alternatively, you can '*escape*' the alias by preceeding the ``rm`` command with a backslash character ``\``::

    berlin% \rm ~/DATA/someStuff/hello.dat

.. _rm-f:

Another useful option for ``rm`` is ``rm -f`` which 'forces' a remove, even if what you are asking it to remove doesn't exist, e.g.::

    berlin% rm -f somethingThatDoesntExist.dat

.. _rm-r:

Finally for ``rm`` for the moment, the option ``-r`` allows you to do a recursive delete (i.e. all directories, subdirectories and their contents). This can be a little dangerous for novice users as you might accidentally delete a whole load of things you didn't mean to, but it is worth knowing about and practicing with. Type the following and make sure you understand what each command is doing::

    berlin% mkdir ~/DATA/newStuff
    berlin% cp ~plewis/msc/*dat ~/DATA/newStuff
    berlin% ls -l ~/DATA/newStuff/
    berlin% \rm -r  ~/DATA/newStuff

.. _cp-R:

Whilst of the subject of recursion, we note the ``-R`` option to ``cp`` which allows a recursive copy, e.g.::

    berlin% mkdir ~/DATA/newStuff
    berlin% cp -R ~plewis/msc  ~/DATA/newStuff

would do a recursive copy of everything in ``~plewis/msc``, including subdirectories, into the directory  ``~/DATA/newStuff`` [#]_.


.. _mv:

We know how to *copy* a file from one place to another, but not how to *move* them. In fact the concept of moving (on the computer) is essentially the same as *renaming*. To move or rename a file in Unix, we use the command ``mv``::


    berlin% mkdir ~/DATA/newStuff
    berlin% cp ~plewis/msc/h*dat ~/DATA/newStuff
    berlin% mv ~/DATA/newStuff/hello.dat  ~/DATA/newStuff/helloo.dat

Check what has happened using ``ls``. You should notice that the file that was called ``~/DATA/newStuff/hello.dat`` is now called ``~/DATA/newStuff/helloo.dat``. As a clearer example of moving a file::

    berlin% mkdir ~/DATA/newStuff2
    berlin% mv ~/DATA/newStuff/helloWorld.dat ~/DATA/newStuff2

Again, check what has happened here using ``ls`` or ``ls -l``.

.. _df:

As the last of these *introductory* commands, we will introduce one to tell you how much disk space is free. This is ``df`` (`disk free <http://en.wikipedia.org/wiki/Df_%28Unix%29>`_). A typical example of this is::

    berlin% df -h .

where the option ``-h`` asks for the information in 'human readable' format (rather than the default 1 KB blocks) and ``.`` (dot) refers to the current directory (the current filesystem in this case). Ones you might be particularly interested in are your home disk and your DATA disk::

    berlin% df -h ~ ~/DATA
    Filesystem            Size  Used Avail Use% Mounted on
    128.40.214.15:/home1/research/plewis
                      4.0G  3.6G  327M  92% /home/plewis
    128.40.214.90:/export/raid_0
                      129G  127G   39M 100% /data/rsu_raid_0


.. _quota:

In the example here, ``/home1/research/plewis`` is of size 4 GB, but 3.6 GB are used (so there is not much space left). On the DATA disk, the disk is larger (129GB) but 127 GB are used (again, not much space). In Remote Sensing, you may well be using large files, so you need to keep an eye on your disk usage. In fact, on the UCL Geography system, we put a quota on your home directory 
which limits the size of data you can keep in there. If you over-run your quota or get near to filling it, you can find some unexpected behaviour when you use the system. This might include not being able to log in. You can check where you are on your quota with::

    berlin% quota -v

If you find one day that you are unable to log in via the windowing system to the Unix machines, this is **most likely**  because you have gone over your quota. To fix it, you will need to log in remotely (next session) and delete or move files that shouldn't be there. 

To avoid this, **you should keep all of your data in the DATA directory** (suitably organised into subdirectories if you don't want to get confused). The ``home`` are is regularly backed up, but the data are is not. However, the data area runs on RAID disks and so should normally be recoverable should teh system go down. We do not keep very frequent backups of the data areas however, so if you delete files, they will generally be gone (so be careful with ``rm -r``!!).

Summary
=======

In this section, you have been introduced to what is pretty much the basic set of Unix concepts you will need to use any Unix-like system (file system, relative and absolute filenames, special symbols and a base set of commands). You will need to become familiar with these, but we do appreciate that it takes time and prictice to do this. You should bear in mind that the commands that you have been shown here are the core tools that you would need on any system to navigate your way around the computer system, to make or remove directories, or to copy or move files. Learning these basics is the one major overhead of Unix, but once you know them, you can make more powerful use of the computer.

As a reminder, the Unix commands learned here were:

 [`alias`_] [`cd`_] [`chmod`_] [`cp`_] [`df`_] [`ls`_] [`mkdir`_] [`mv`_] [`pwd`_] [`quota`_] [`rm`_] [`rmdir`_]

with a few options:

  [`cp-R`_] [`ls-l`_] [`rm-f`_] [`rm-i`_] [`rm-r`_]

The Unix symbols we come across are:

 [``/``: `slash`_] [``\``: `backslash`_] [dotdot: `..`_] [dot: `.`_] [tilde/twiddle: `~`_] [star/wildcard: `*`_] [single wildcard: `?`_]

You will need to practice using these to become familiar with them, and you will need to become familiar with them for the rest of the course, so you need
to put the time in early on to do this.

In the next section, we will move onto a few more 'advanced' Unix concepts and introduce some useful tools to you.


.. [#] An often useful more advanced alternative is the `pair of commands <http://en.wikipedia.org/wiki/Pushd_and_popd>`_ ``pushd`` and  ``popd``.

.. [#] Often, using the command ``tar`` (which stands for 'tape archive', but really is a general archiving command) can be useful for this, but it can be `inefficient on some (Windows) systems <http://en.wikipedia.org/wiki/Tar_%28Unix%29>`_ and some people don't like too many pipes (we will learn pipes in the next section). You can achieve the above ``cp -R`` command with `tar` with the command: ``berlin% cd ~plewis; tar cvzf msc | (cd ~/DATA/newStuff; tar xvzf -)`` which looks a lot more complex, but has the advantage of compressing the data whilst copying it. It will also maintain the original modification date information for the files.
