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
Some more Unix and associated tools
===================================

UNIX Command Structure, Data Flow and File Manipulation
--------------------------------------------------------

The previous section dealt with the basic tools of Unix. Now, we will look at a few useful tools you have access to and some slightly more advanced concepts that again enable you to do more with the computer.


Data Flow : stdin and stdout
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Within UNIX all information is stored in files. Programs are told to read from and write to these files either by redirecting their input and output, or by modifying their action through the use of command line arguments or options. The channels through which the data flows to or from are known as streams. In the special case where data flows directly from one program into another, these channels are known as pipes.

By default, with no options or arguments to specify otherwise, most commands will read their input form the keyboard and write their output to the screen. The data channels which attach the keyboard and the screen to the program are known as the standard input (stdin) and the standard output (stdout) respectively.

Stdin and stdout can be redirected to and from files rather than the keyboard or screen using the UNIX ``<`` ("read from) and ``>`` ("write to") symbols::

    berlin% ls -l /var > listing

where the standard output of the ls command was redirected into the file 'listing'. 

The command ``cat`` may not be used to view the contents of a text file if it is directed to take its input from that file e.g. ::

    berlin% cat < listing
    total 200
    drwxr-xr-x  2 root root   4096 Feb  7  2011 account/
    drwxr-xr-x  2 pcap pcap   4096 Feb  8  2011 arpwatch/
    drwxr-xr-x 12 root root   4096 Oct  1  2009 cache/


shows the results of the previous ``ls`` command. Here the output of cat is not redirected, and so its output goes to the screen. Equally a copy of the file 'listing' could have been made by redirecting the output to another file, 'listing2', say::

    berlin% cat < listing > listing2 
    berlin% ls -l list*
    -rw-rw-r-- 1 plewis plewis 1287 Sep 26 13:48 listing
    -rw-rw-r-- 1 plewis plewis 1287 Sep 26 13:48 listing2

The behaviour of ``cat`` can also be modified with options ``cat -n < listing``, for instance, would place a line number at the start of each line of output, cat will be described in more detail below.

stderr - '>&'
~~~~~~~~~~~~~

There is one more channel which every program has by default; its standard error channel, stderr. This is where the program write any error messages to notify the user of abnormalities, or other information to notify status which is not directly part of the output of the program. As with stdout, unless specifically redirected stderr writes to the screen. To redirect stderr separately from stdout the UNIX ``>&`` symbol must be used, although in a somewhat more complicated fashion than ``>`` alone. See the `manual page for csh (the C-shell) <http://www.grymoire.com/Unix/Csh.html>`_ for more details (remember that there are other shells that you might use, such as `bash <http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29>`_).

Appending to a file - >>
~~~~~~~~~~~~~~~~~~~~~~~~

If a file already exists when ``>`` is used to write data to it, then the contents of that file will be overwritten with the new data. If the file does not exist then is will be created, so long as the user has permission to write to a file. Sometimes it is useful to add data to the end of a file, rather than create a new file. This may be achieved using the ``>>`` symbol.

For instance::

    berlin% ls -l /etc >> listing

would append a listing of the directory ``/etc`` to the file ``listing`` without affecting the listing of ``/var`` already there.

Pipes, |
~~~~~~~~

One of the most powerful features of UNIX is the ability to take the output of one program and pass it straight to the input of another, without the necessity of writing intermediate files. This process is known as piping, and is achieved using the ``|`` symbol::

    berlin% ls -l /var | cat -n
     1	total 200
     2	drwxr-xr-x  2 root root   4096 Feb  7  2011 account/
     3	drwxr-xr-x  2 pcap pcap   4096 Feb  8  2011 arpwatch/
     4	drwxr-xr-x 12 root root   4096 Oct  1  2009 cache/
     5	drwxr-xr-x  2 root root   4096 Apr 29 03:28 crash/
 

Here the standard output from the ls command is piped into the standard input of the cat command, which could be running with the ``-n`` option to number the lines that it outputs. The output of the cat could have been redirected or appended to another file, or even piped into another program such as more, which prints its input to the screen one screenful at a time, allowing the user to read long files (see the Useful Commands handout). In this way large quantities of data can be processed in very complicated ways using minimum disk space. 

Similarly to stdout, stderr can also be piped - in this case the UNIX symbol is ``|&``.

*NOTE* : The characters ``> < | &`` should not be used in filenames, as they have special meanings to the shell described above. 

 
Changing passwords, mail forwarding, accessing WTS
--------------------------------------------------

Some things it is useful for you to know:

.. _password:

- You should change your password regularly. To do this on the UNIX system, use the command passwd. You will be prompted for current and new passwords. Should you forget your password, you will need to contact the system manager, Chris Knell.

.. _mail:

- If you want to forward mail from your UCL Geography account to another account, you can create a file called ``.forward`` (note the dot) in your home directory that contains the email address you want to fwd email to (make sure you don't do this recursively or you can make the network go crazy).

- If you want to access the UCL PC clusters from the UNIX workstations, you can currently do so (in a java enabled browser) by following the instructions available from `ISD wts-web <http://www.ucl.ac.uk/isd-extra/common/windows/wts-web/>`_.
- If you are not using a java-enabled browser, you should type:: ``wtsetup`` at the command prompt, the *first* time you run WTS. Thereafter, type: ``wts &`` at the prompt. We will see what the ``&`` means below.
- If you want to use WTS from outside of College, see `ISD remote <https://www.ucl.ac.uk/isd/students/windows/wts/access/remote>`_ for further information, or use a java enabled browser as above.
- Students can find further information about connection to the UCL system from `ISD offsite <https://www.ucl.ac.uk/isd/students/offsite>`_. There are many useful services that include a `Drop Box <https://www.ucl.ac.uk/isd/students/mail/dropbox>`_ for file transfer.
- You can find useful information about UCL Unix services, again from `ISD unix <https://www.ucl.ac.uk/isd/students/unix>`_. You can normally access two machines, ``socrates.ucl.ac.uk`` and ``plato.ucl.ac.uk`` (although these are currently down and I cannot check them at the time of writing). As a side note, to check whether a computer is alive and accessible, you can use `ping`_.
- If you want to transfer files between Geography computers and other computers outside of the LAN, you should use `sftp`_ into ``shankly.geog.ucl.ac.uk``. If you do not have software that allows sftp, you will not be able to do this directly. If you can use sftp, you can use put and get to transfer files as in (non-secure) ftp (some tools will have drag-and-drop features). If you do not have sftp client software, search for some on the internet or look `at this list <http://en.wikipedia.org/wiki/List_of_SFTP_clients>`_. 
- Another (slower) way to transfer files is to use WTS, in which you can mount the local file system (this is by default the ``H:`` drive in WTS). You can directly transfer files within Windows by just copying from the ``H:`` drive, but you can also use ``sftp`` tools within WTS to transfer elsewhere.
- If you want to access the UNIX machines from outside of the lab, there are several avenues for this. If you only require an interactive session on the Geography Unix machine and do not need to use any 'pop up' windows (e.g. ``envi``, ``firefox`` or any graphing packages) then you can use any `ssh`_ `client software <http://www.openssh.com/>`_ to do this. 
    - From any linux/Unix machine, including Mac OS-X, this just involves running ``ssh`` from a terminal. 
    - From Windows, start the client software (e.g. putty) and connect through that.
- If you want to to be running any X11 windowing, this is simple on any linix/Unix machine as your windowing system will be using X11 anyway. You just need to make sure that the remote machine 'knows' where to open windows. This is achieved using e.g. ``ssh -X socrates.ucl.ac.uk``. It is not much more complex under OS X, but you have to first start up ``X11`` which you will find in the ``Utilities`` folder under ``Applications`` (along with ``Terminal``). To start an X11 session of a remote machine then use ``ssh -Y socrates.ucl.ac.uk``. Remember: use ``-Y`` from a mac, but ``-X`` otherwise. The first time you connect two computers using ``ssh`` you will be prompted to confirm that that was what you intended to do. You will also be prompted for your password.
- If you want to run a process on a remote machine, you can use ``ssh`` for that as well (see `ssh`_).
 -- UCL ISD have set up a secure `VPN <http://www.ucl.ac.uk/isd/staff/network/vpn>`_ for remote acvess, but this seems to be available only for staff at present.

Some useful Unix Commands
-------------------------

Here, we give a list and some basic text on some core Unix commands that you should become aware of.

.. [`awk`_] [`cat`_] [`grep`_] [`info`_] [`man`_] [`more`_] [`less`_] [`paste`_] [`ping`_] [`sed`_] [`sftp`_] [`ssh`_] [`vi`_]


.. _man:
.. _info:

man info
~~~~~~~~

The traditional place to get help information on Unix commands is the 'man' (manual) page that you access with the command ``man``::

    berlin% man ls

This will bring up the manual page for the command ``ls``. There are subtleties to ``man``, including the use of sections::

    berlin% man -s 3 exec

which looks explicitly in section 3 here ('Linux Programmer's Manual') for ``exec``. See::

    berlin% man man

for more details. Depending on system setup, you will often get the same or better help using the command ``info``::

    berlin% info info

which accesses the Gnu manuals. You can just type ``info`` for a list.

Note that when you enter ``man`` or ``info`` paging takes place using ``more`` or more commonly ``less``.

.. _more:

.. _less:

more or less
~~~~~~~~~~~~

``more`` or more often ``less`` are Unix utilities for paging information in the terminal. See ``man less`` etc. The basic you need to know:

* ``q`` to quit
* ``SPACE`` (spacebar) for page down
* ``b`` to page up.
* ``RETURN`` (return/enter) to go down one line at a time (``u`` to go back one line).
* ``/`` for search (as with ``vi``)

The main difference you would probably notice between ``less`` and ``more`` is that ``more`` quits when you reach the end of the file, but you have to explicitly quit from ``less``. 

Note that you can enter ``vi`` from these commands, with ``v`` (and you may sometimes do that accidently, so be aware of it).


.. _cat:

cat
~~~


We saw above that ``cat`` cat be used to send a file from ``stdin``  to ``stdfout`` but its more often used to 'concatenate' files (join sequentially, line by line). For example::

    berlin% cat file1 file2 > file3

would copy file1 and file2 one after the other into a new file, file3. If ``-`` is specified in the sequence of files to be concatenated, then the standard input is read at that point. For example:: 

    berlin% cat file2 | cat file1 - file3 > bigfile

would result in bigfile containing the contents ``file1``, ``file2`` and ``file3`` in sequence. 

.. _paste:

paste
~~~~~

A command that is quite complementary to ``cat`` is ``paste`` which pstes files together 'vertically' rather than horizontally like ``cat``. For example::

    berlin% cat > file1.dat
    hello there
    hello again
    hello
    ^D
    berlin% cat > file2.dat
    you
    me
    another
    again
    ^D
    belin% paste file1.dat file2.dat
    hello there	    you
    hello again	    me
    hello	    another
	    again


Notice that the 4th line of the file only contains ``again``, from the second file.

.. _sed:

sed
~~~


``sed`` is a 'stream editor` which migth nmot sound like much, but is extremely powerful. See `any tutorial <http://www.grymoire.com/Unix/Sed.html>`_ for full use, but a few quick examples should suffice to demonstrate some key uses::

    berlin% echo "hello world" | sed 's/hello/goodbye cruel/'
    goodbye cruel world
    berlin% echo "hello world" | sed 's/o/oo/'
    helloo world
    berlin% echo "hello world" | sed 's/o/oo/g'
    helloo woorld

In these examples. we use ``s`` to substitute text that is delimited by `//` by other text. This is done for *each line* of the input file/stream (only one here), for the first occurrance of the string. If you see '/g' at the end of the ``sed`` statement, then the substitution is 'global', so here, every timer we see 'o' we replace it by 'oo'.

.. _awk:

awk
~~~


See also ``gawk``, the gnu version of ``awk`` (or ``nawk`` etc.). This is a very powerful & simple pattern matching utility. The usual use of it is to apply some 'c-like' statement for every line of a text file. Probably the most common use is something like::

    berlin% echo 1 2 3 4 5 | gawk '{print $3}'
    3

where we use it to print the 3rd column of text. There are many `tutorials <http://www.grymoire.com/Unix/Awk.html>`_  and books on this, and again, its worthwhile knowing at least the basic use of this language.

.. _grep:

grep
~~~~

Another core unix utility that applies pattern matching to text files/streams, `called grep <http://en.wikipedia.org/wiki/Grep>`_. A few examples will suffice to show its use::

    berlin% ps auxww | grep plewis | gawk '{print $2}'
    1101
    1102
    1103

Here, we run the command ``ps`` to get information on processes running on the machine, then we use ``grep`` to filter this so that we only see lines which have ``plewis`` in them (so now we have only processes that involve ``plewis``) then finally, we apply a filter using `awk`_ to print out the second column, which is the process IDs (PIDS). If we looked carefully at the output of::

    berlin% ps auxww | grep plewis 
    plewis    1188  0.0  0.0  10488   888 pts/2    R+   14:22   0:00 ps auxww
    plewis    1189  0.0  0.0   6060   596 pts/2    S+   14:22   0:00 grep plewis
    plewis   32024  0.0  0.0 108428  2448 ?        S    13:24   0:00 sshd: plewis@pts/1

we would see that this includes information about the command ``grep plewis`` and the ``ps`` command we are running, so if we want a list of PIDs for processes other than these, we could use::

    berlin% ps auxww | grep plewis | grep -v 'ps auxww' | grep -v grep | gawk '{print $2}'
    1230
    32022
    32024

which is probably what we want in such cases. The option ``-v`` filters lines **not** including the pattern we state.

process control
----------------

foreground and background
~~~~~~~~~~~~~~~~~~~~~~~~~~

When you start a process that opens another window, you may have noticed that no prompt was returned and that any subsequent typing in the parent window was ignored until you exited the command (or it finished some other way). This was because tool you started has taken over input to and output from the parent window, or more accurately, the shell running the window. In this state the program you started is said to be running in the foreground - that is no further processes can be started from that window/shell until textedit relinquishes control.

As an example, try::

    berlin% xv


Now try typing another command such as ``ls``. It won't work because the ``xv`` command is still running in the foreground (well, it *will* work when you quit ``xv`` which might be some time later & could be rather confusing).

There are two ways to allow further action from the parent window:

* kill the ``xv`` process
* run ``xv`` in the background

starting a job in the background
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When the program (or process, as it is known) runs in the background, it dissociates itself form the parent shell from which it was started, and allows that shell to carry on receiving input from the keyboard as usual. To start a process in the background, us an ampersand, '&' is placed at the end oif the command line e.g.::

    berlin% xv &

The systems responds with a line of information about the new background process, followed by the prompt - something like::

    [1] 3568

The [n] indicates this is the nth job to be started in this shell, and n is the unique job number by which the process may be referenced within that shell (window). The second number on the line (3568) is known as the process ID (PID) of the program. This is the number by which the central processor of the workstation refers to the job. This number is unique to the program you have started, and may be used in any window to refer to this process, as will be see.


Stopping a job to place it in the background - ^Z and bg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If the process you wish to place in the background is already running, it can be stopped using ``^Z`` (control-z). The prompt will then return, and the job is placed in the background using the ``bg`` command:: 

    berlin% xv

so ``xv`` is now running in the foreground. Then::

    ^Z
    berlin% bg
    [1] 3568

so ``xv`` is now running in the background, and the prompt should appear again so you can type new commands.

Killing a job running in the foreground 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Normally, you can terminate a job running in the foreground with ``^C`` (control and ``c``). If that does not work, try ``^Z`` as above, followed by ``jobs`` to see the number of the job to be killed, then kill it (see below). 


Job control within the Shell 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Within its parent window, a job may be referred to in certain commands a ``%n``, where ``n`` is the number that was given in square brackets when the process was started. 

The job may be brought back into the foreground using:: 


    berlin% fg %n

no prompt will be returned until either the job finishes or is placed back into the background. 

The job may be killled using:: 

    berlin% kill %n

or::

    berlin% kill -9 %n


if it refuses to die the first time. 

The priority of the job may be changed to let other people share the workstation::

    berlin% renice +19 %n 
    0: old priority 0, new priority 19

A list of jobs currently running within the shell may be obtained using the ``jobs`` command. On some systems, ``jobs -l`` will give the most useful information.

 
Killing or changing the priority of a job from outside its parent shell
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you made a note of the PID of each process when it started, then ``kill`` and ``renice`` can be used as before, but using the PID instead of job number:: 

    berlin% renice +19 3568
    3568 : old priority 0, new priority 19
    berlin% kill 3568

If you didn't note the PID, there are two ways to find it:

* run the ``top`` command in another window and look at the process in the display
* use ``ps`` (e.g. ``ps auxww``)

top
~~~

``top`` is a program used to display the processes currently using the most CPU (processing capacity) on a workstation. Typing top in a shelltool should result in a display similar to:: 

    last pid : 3609; load averages : 0.00, 0.00, 0.00 03:47:19

    49 processes : 48 sleeping, 1 running

    Cpu states : % user, % nice, % system, % idle

    Memory : 11984K available, 11812K in use, 172K free, 2572K locked

    PID Username PRI NICE SIZE RES STATE TIME WCPU CPU COMMAND

    3598 plewis   15 19 125K 99K run 9:20 12:49% 0.95% xv
    3609 plewis   26 0 225K 472K run 10:29 7.69% 0.22% textedit
    3607 plewis   36 0 422K 432K sleep 0.00 3.23% 0.12% csh 

Look for your program in the far right column, and get its PID from the far left column. Typing i may reveal more processes if yours is not shown. Jobs can actually be killed (``k``) and reniced (``r``) from inside ``top`` - see man page for more details.


ps
~~


``ps`` is similar to ``top``, but just lists the processes rather than providing a continuously updated display::

    berlin% ps auxww | less
    USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
    root         1  0.0  0.0  10368   696 ?        Ss   Sep13   0:04 init [5]
    rpcuser   4034  0.0  0.0  10180   796 ?        Ss   Sep13   0:00 rpc.statd


Sharing the workstation - nice
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Whenever a job that will either use a lot of the machines processing power (such as an image processing command) or take a long time to run is started, it must be 'nice'd up'. That is, the priority of the job must be set so that other users can make use of the workstation whilst your job is running. This is achieved using either the renice command, as in section 6.4 and 6.5, or preferably by using the nice command as the job is started::

    berlin% nice +19 xv &
    [2] 3610

This starts ``xv`` in the background, and sets its priority to allow fair use of the machine by other people. In fact, ``xv`` is not a process that would normally need to be niced, as, unless image processing operations are being performed it usually takes virtually no processing power. It is used here simply as an example. 




remote access
-------------

ping
~~~~

.. _ping:

Ping sends some test packets to a remote computer and reports on what is returned. Normally, e.g. to check the status of a machine called ``socrates.ucl.ac.uk`` you just type::

    ping socrates.ucl.ac.uk

which will report e.g.::

    PING socrates.ucl.ac.uk (144.82.100.160) 56(84) bytes of data.

If nothing happens for some time, the machine is probably not available (because it is down or the network in unreachable). You can wait for a timeout, or use ``^C`` (Control (ctrl) and C (capital C) at the same time) to quit the command. To limit the call to a certain number of attempts, use::

    ping -c 10 socrates.ucl.ac.uk

If the response is::

    --- socrates.ucl.ac.uk ping statistics ---
    10 packets transmitted, 0 packets received, 100.0% packet loss

Then you can't currently access the machine.

.. _sftp:

sftp
~~~~

Secure file transfer using `ssh`_ protocols. If working from a terminal (shell) and you want to transfer files from your local machine to a machine e.g. ``shankly.geog.ucl.ac.uk``, ``cd`` to where the files are on the local machine, then type::

    sftp shankly.geog.ucl.ac.uk
    
at which point you will normally be prompted for a password. If the username on the local and remote machines are different, you should use::

    sftp ucfaabc@shankly.geog.ucl.ac.uk

if your username (on the remote computer, ``shankly.geog.ucl.ac.uk``) happens to be ``ucfaabc``.

You can then use the `limited command set <http://kb.iu.edu/data/akqg.html>`_ within ``sftp`` to change directory etc. and copy the files to or from the remote machine. A typical session then would be something along the lines of::

    sftp> cd whereIWantToPutTheData
    sftp> put theFileIWantToTransfer.dat

to copy the local file ``theFileIWantToTransfer.dat`` into the directory ``whereIWantToPutTheData`` on the remote machine. Similarly to pull a file from the remote machine, use ``get`` rather than ``put``.

Use ``exit`` to exit the ``sftp`` session.    

.. _ssh:


ssh
~~~


Securely connect ('log in') to a shell on a remote computer. To set up an interactive session, from a terminal or ssh client type::

    home% ssh ucfaabc@shankly.geog.ucl.ac.uk

and respond to any confirmation request (the first time you connect two machines) and the request for your password. 

If you wish to run a session that uses X11, you need to set X11 tunneling::

    home% ssh -X ucfaabc@shankly.geog.ucl.ac.uk

on most unix/linux machines, or::

    home% ssh -Y ucfaabc@shankly.geog.ucl.ac.uk

from OS X. 

From a Windows machine, you should be able to connect using a client such as `putty <http://www.chiark.greenend.org.uk/~sgtatham/putty/>`_, but this does not directly allow X11 sessions. To do that, you need some X11 software (on the Windows machine) such as `exceed <http://faq.rutgers.edu/?q=node/836>`_. You can purchase that software, or at no cost, use a WTS session (see above) to start up `exceed <http://faq.rutgers.edu/?q=node/836>` and then use e.g. putty (or tools in exceed) with `X11 forwarding <http://faq.rutgers.edu/?q=node/838>`_. There are several alternatives to this from a Windows machine, one of which is to set up a unix environment within windows using `cygwin <http://www.cygwin.com/>`_ but that might be too complex for novice users. Another  is to make your Windows computer `dual boot <http://www.google.co.uk/search?q=windows+dual+boot&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a>`_ and install a linux system such as `ubuntu <http://www.ubuntu.com/>`_ on it. Yet another is to run linux as a `virtual machine <http://www.lifehack.org/articles/technology/beginners-guide-run-linux-like-any-other-program-in-windows.html>`_ on top of Windows (or `the other way around!i <http://www.virtualbox.org/>`_). Another alternative is `Xming <http://www.straightrunning.com/XmingNotes/>`_ that will run X11 on top of windows. Please note that whilst there are all of these potential solutions, we do not endorse or provide support for any particular solution. If you want to be able to do this and think it would be useful, try it out yourself and use the internet for resources to help you solve any problems you come across. If you have particular problems you think are connected with the UCL end of things, you can try asking Chris Knell, the Geography System Manager, or ISD (if it is a UCL issue), or at a push, Professor Lewis in his office hours.

**Important**:
Note that you **cannot** use ``ssh`` (or ``sftp``) to connect to *any* of the UCL Geography computers, as we only have a small number open to the UCL firewall (such as ``shankly.geog.ucl.ac.uk``) and the machines we do have open are not ones you would normally want to do any processing on (or at least, we don't want *everyone* processing on these gateway machines, as noone else will be able to get in). You will *normally* have to use ssh to get on to one of these firewall gateway machines, *then* ``ssh`` (normally ``ssh -X`` if you want to maintain X11 port forwarding) from there to a machine (e.g. one in the classroom) to do any processing. This might seem a little 'roundabout', but you will soon get used to it and it is like this for good security reasons.

**N.B.** if your username is different on the two machines, use e.g. ``ssh -X ucfaabc@socrates.ucl.ac.uk`` or  ``ssh -X socrates.ucl.ac.uk -l ucfaabc`` to give the correct username for the remote machine (the one you are trying to log on to), otherwise you can just use ``ssh -X socrates.ucl.ac.uk``. 

Once you (think you have) established a remote session with X11, you should test it out, trying to open a simple application such as ``xclock`` or ``xv`` or ``xeyes`` from the remote machine onto your local machine.

If you are sure you are on a secure machine, you can set things up so that you don't have to keep typing the password when you connect (see `here <http://linuxproblem.org/art_9.html>`_) but remember that anybody else will be able to connect those machines without a password.

Finally, if what you want to do with ``ssh`` is not to run an interactive session, but to run a process on the remote machine (e.g. for some parallel processing), then you would normally use ``ssh -f`` for this, with the option ``-X`` (or ``-Y`` for OS X) if the processing requires X11. A simple xample would be, get a listing of your home directory::

    home% ssh -f ucfaabc@shankly.geog.ucl.ac.uk "ls -l /home/plewis"

This will execute the sequence of commands in quotes on the remote machine, then, when completed, terminate the session (that is what the ``-f`` flag does). If you want to ssh from that machine onto another (to run a process) that is a little more involved.

One way to do this would be e.g.::

    home% ssh -f shankly.geog.ucl.ac.uk 'ssh -f berlin.geog.ucl.ac.uk "uname -a;pwd; cd /home/plewis ; ls -l"'

which will ``ssh`` onto ``shankly.geog.ucl.ac.uk`` and from there run an ``ssh`` process onto ``berlin`` and then run the requested sequence of commands. Note that in this case you will have needed to previously `ssh`d from ``shankly`` to ``berlin`` to have responded to the authentification request.  This is a littler convoluted, especially the use of quotes here but is it feasible and sometimes useful to do this. You are much more likely to make use of this sort of command directly from within the UCL Geography system, in which case you do not need multiple levels of ``ssh`` calls to get through the firewall. 

.. _vi:

Some editors
------------

vi
~~


``vi`` is a generic Unix tool for editing text files (it is what I am using to type this now). It is available on *all* Unix systems, either as ``vi`` or the enhanced ``vim`` and/or easily accessible from the internet. It has a major advantages of being: simple (once you learn the basics); ubiqiuotous (get it everywhere); and that you do everything in a terminal (i.e. no overhead costs for popping up X11 windows). This latter point can be a significant advantage if you ever (which you will) find youself trying to edit some control file on a remote computer over a very low bandwidth / slow connection. For this last reason alone it is worth newcomers to Unix learning the basics of the tool, even iof they choose some alternative as their day to day text editor.

We will go through some exercises in class, but you can also follow a good short tutorial on this called `vi for smarties <http://www.jerrywang.net/vi/>`_.

The *key* ones you need to remember are:

* Esc to go into command mode
* arrows or ``hjkl`` to navigate (left, down, up, right)
* ``/`` to search (``n`` for next, ``N`` for prev) 
* ``:N`` for going to line number ``N`` 
* ``:w filename`` for write to filename (or just ``:w`` for write)
* ``:q`` for quit (or ``:q!`` for force quit, or more often ``:wq`` for write and quit)
* ``i`` and ``a`` for insert/append model (enter text)
* ``x``, ``dw``, ``dd`` for delete character, word, line (``Nx``, ``Ndw``, ``Ndd`` for deleting ``N`` times)
* ``s`` for substitute
* ``J`` for deleting newline

Emacs
~~~~~

Another common/useful editor is emacs. This is perhaps a little easier to learn than ``vi``. There are `various tutorials <http://www2.lib.uchicago.edu/keith/tcl-course/emacs-tutorial.html>`_  for this.

Nedit
~~~~~~

Yet another is `nedit <http://www.nedit.org/>`_. Take you pick of these or other editors, but its worthwhile learning the basics of ``vi``, just in case you ever need such a tool (and its very fast to use once you get used to it).


