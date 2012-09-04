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


