Coursework
==========

Submission
----------
You need to submit a hard copy to room G03 in UCL Pearson Building *and* an electronic copy to TurnItIn via the module Moodle page, by 12:00 16 Jan 2012 (the monday after exam week).

You must work individually on this task. If you do not, it will be treated as plagiarism. By reading these instructions for this exercise, we assume that you are aware of the UCL rules on plagiarism. You can find more information on this matter in your student handbook. If in doubt about what might constitute plagiarism, ask one of the course convenors.


Summary of coursework requirements
----------------------------------

Assessed Exercise: Part 1 (of 3)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The `first task <http://www2.geog.ucl.ac.uk/~plewis/geogg122/vectorMask.html#assessed-exercise-part-1-of-3>`_ you must complete is to produce a dataset of the proportion of HUC catchment 13010001 that is covered by snow for the year 2005. The dataset you produce must be for every day over the year.

* You would probably want to use a daily snow product for this task, so make sure you know what that is.
* You will notice from the figure above that there will be areas of each image for which you have no information. You will need to decide what to do about that.
* The simplest thing might be to produce a mean snow cover over what samples are available, but there are certainly much better ways of filtering these? missing values?
* You will notice that if you use MODIS data, you have access to both data from Terra (MOD10A) and Aqua (MYD10A), which potentially gives you two samples per day.
* Whilst you only need to produce an average daily value for the catchment, there might be some value in trying to estimate snow presence/absence for each pixel in the catchment (e.g. so you could do spetially explicit modelling with such data). I stress that this is not strictly necessary, but would be an interesting thing to do if you feel able.

Assessed Exercise: Part 2 (of 3)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Your `second task <http://www2.geog.ucl.ac.uk/~plewis/geogg122/DelNorte.html#assessed-exercise-part-2-of-3>`_ for the assessed practical then, is to develop a simple hydrological model capable of describing the observed flow data. 

You should run and test the code using appropriate climate data and snow cover data for HUC catchment 13010001.

Your code should include a function that can be called with an array of parameter values (so, it would contain tempThresh, K, and p if you follow the example above). This function must be capable of calculating the predicted flow data (i.e. accum here).

Your code should include another function that calculates the mismatch between the modelled flow data (accum here) and the observed data.

You should explore and describe what the impact of the model parameters is, giving some relevant values of mismatch and graphs.

If you have been unable to complete the first part of the practical, you should proceed with this section, using the data provided above, then revisit the snow proportion calculation later if time allows.

There are many ways in which this model could be criticised, so do try to think through all of the assumptions that are being made in developing a model of this sort. If you have time, try to develop some modifications to the model that might improve operation, but be careful not to put too many new parameters into it. Also think through what the uses of such a model might be.

Assessed Exercise: Part 3 (of 3)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Your `third task <http://www2.geog.ucl.ac.uk/~plewis/geogg122/spectral.html#assessed-exercise-part-3-of-3>`_ is to apply an optimal estimation framework within python to calibrate the parameters of the hydrological (snow) mode you have built in a previous exercise.

You must quantify the goodness of fit between your measured flow data and that produced by your model.

If you wish to go beyond the basic requirements for this part of the practical, probably the most fruitful thing to do would be to attempt to validate the model and the parameters that you have obtained by applying them to data from a year that is independent of that used for the calibration (i.e. not 2005).


Structure of report and balance of marks
----------------------------------------

The required elements of the report are:

* Introduction (5%)
* Materials and Methods (5%)
* Pseudocode (10%)
* Code (60%)
* Results (10%)
* Discussion/Conclusions (10%)

The figures in brackets indicate the percentage of marks that we will award for each section of the report.

We judge the first task to be more difficult than the other two, so will award marks in the proportion 50:25:25 for work referreing to these tasks.

Introduction
~~~~~~~~~~~~
This should be of around 2-3 pages. 

It should introduce the purpose of the study, being at a base level, 'to build and calibrate a snow/hydrological model in python'. 

It should provide some background to building models of this sort (their purpose/role) and include some review of the types of models that might be built, with reference to the literature (journals). 

Materials and Methods
~~~~~~~~~~~~~~~~~~~~~
This should be no more than 3 pages, including figures. 

It should introduce the study site, giving general site characteristics, with appropriate figures.

It should provide an overview of the data used in the study.

It should provide an overview of the model that is constructed here, explaining the role of each parameter.

It should explain the way in which model calibration is to be undertaken.

It should include a rationale to any variation to the base level experiments/model/codes that you might have done.

Experiments
~~~~~~~~~~~
The experimental part of the work covers the remaining sections. You can choose to have separate sub-sections for each of the three tasks, or to group them together in the report. If you do group them together, it should be clear to the reader/marker which part corresponds to which task. 

Pseudocode
~~~~~~~~~~
For each piece of code that you write to tackle each of the three tasks, you **must** include some pseudocode. 

This should provide a description of the inputs and outputs, and describe the ipurpose and main flow of the code. You can choose to split up the pseudocode into parts for each method/function that you define, but you must provide an 'overview' piece that gives the flow of how they fit together.

You should look back at the notes on `psedocode <http://www2.geog.ucl.ac.uk/~plewis/geogg122/dem2.html?highlight=pseudocode#raindrops-on-roses-pseudocode>`_, which provides links through to further material and examples.

You should be able to use material from your pseudocode in writing your code documentation and comments (see below), but you **must** also provide this separate pseudocode section in your report.

Code
~~~~

Some guidelines on the requirements for the code are given below. You should read through these carefully, noiting what is required of you. I have tried to give examples of what would be adequate/good/excellent where appropriate. As a broad guideline though, if you have a piece of working or *very nearly* working code for all parts, that achieves the task requirements, and that has adequate documentation and referencing (see section on plagiarism) then you should be able to get a pass mark for the code (i.e. something in the 50-59% range). Failing to meet these core requirements will lead to a proportionately worse mark. For a good mark (60-70%), you should have done a good job of all of these elements (so, good documentation, well-written, clear code with good functionality and structure). An excellent mark (70-100%) is achievable for excellent documentation etc., but would normally require that you have gone some way beyond the basics of what is required of you in these tasks. This latter category is there to give students credit for putting extra effort into the work, beyond the base level required. 

Results
~~~~~~~
You should present results from each section. This will normally be the main output of each task, paying attention to specific items that are required (see text above). Results should be presented in graphical and tabular form where appropriate (e.g. snow cover, measured and predicted flow). For snow cover and measured and predicted flow, you **must** also provide summary statistics (min, max, mean, standard deviation at least). Any graphs and tables should be appropriately labelled.

Discussion/Conclusion
~~~~~~~~~~~~~~~~~~~~~
This section should be around 2 pages. It should provide a discussion/ analysis of your results and you should draw appropriatre conclusions from these. 

You can also use this section to critique the model/data/methods, and suggest ways that you would improve things. If you do this, you *must* give some indication of how that would be achieved. You will get no credit for simply saying 'next time I would make the code more efficient', for example. 
 
Very good/excellent marks would normally require you to cite appropriate literature.

Computer code
-------------

General requirements
~~~~~~~~~~~~~~~~~~~~

You will obviously need to submit computer codes as part of this assessment. Some flexibility in the style of these codes is to be expected. For example, some people might prefer to have separate codes for each of the three tasks. Others might write a class that encompasses the functionality for all tasks. Some poeple might have multiple versions of codes with different functionality. All of these, and other easonable variations are allowed. 

All codes needed to demonstrate that you have performed the core tasks are **required** to be included in the submission. You should include **all** codes that you make use of in the main body of the text in the main body. Any other codes that you want to refer to (e.g. something you tried out as an enhancement and didn't quite get there) you can include in appendices.


All codes should be well-commented. Part of the marks you get for code will depend on the adequacy of the commenting.

Degree of original work required and plagiarism
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you use a piece of code verbatim  that you have taken from the course pages or any other source, you **must** acknowledge this in comments in your text. Not to do so is plagiarism. Where you have taken some part (e.g. a few lines) of someone else's code, you should also indicate this. If some of your code is *heavily based on* code from elsewhere, you must also indicate that.

Some examples. You may recognise this snippet of code from the section `Modelling delay in a hydrological network <http://www2.geog.ucl.ac.uk/~plewis/geogg122/DelNorte.html#modelling-delay-in-a-hydrological-network>`_.

The first example is guilty of strong plagiarism, it does not seek to acknowledge the source of this code, even though it is just a direct copy, pasted into a method called `model()`::

    def model(tempThresh=9.0,K=2000.0,p=0.96):
        '''need to comment this further ...

        '''
        import numpy as np
        meltDays = np.where(temperature > tempThresh)[0]
        accum = snowProportion*0.
	for d in meltDays:
            water = K * snowProportion[d]
            n = np.arange(len(snowProportion)) - d
            m = p ** n
            m[np.where(n<0)]=0
            accum += m * water
        return accum


This is **not** acceptable.

This should probably be::

    def model(tempThresh=9.0,K=2000.0,p=0.96):
        '''need to comment this further ...

	This code is taken directly from 
        "Modelling delay in a hydrological network"
	by P. Lewis http://www2.geog.ucl.ac.uk/~plewis/geogg122/DelNorte.html   
        and wrapped into a method.
        '''
        # my code: make sure numpy is imported
        import numpy as np

        # code below verbatim from Lewis
        meltDays = np.where(temperature > tempThresh)[0]
        accum = snowProportion*0.
        for d in meltDays:
            water = K * snowProportion[d]
            n = np.arange(len(snowProportion)) - d
            m = p ** n
            m[np.where(n<0)]=0
            accum += m * water
        # my code: return accumulator
        return accum

Now, we acknowledge that this is in essence a direct copy of someone else's code, and clearly state this. We do also show that we have added some new lines to the code, and that we have wrapped this into a method. 

In the next example, we have seen that the way `m` is generated is in fact rather inefficient, and have re-structured the code. It is partially developed from the original code, and acknowledges this::


    def model(tempThresh=9.0,K=2000.0,p=0.96):
        '''need to comment this further ...
   
        This code after the model developed in 
        "Modelling delay in a hydrological network"
        by P. Lewis 
        http://www2.geog.ucl.ac.uk/~plewis/geogg122/DelNorte.html        

	My modifications have been to make the filtering more efficient.
        '''
        # my code: make sure numpy is imported
        import numpy as np

        # code below verbatim from Lewis unless otherwise indicated
        meltDays = np.where(temperature > tempThresh)[0]
        accum = snowProportion*0.

        # my code: pull the filter block out of the loop
        n = np.arange(len(snowProportion))
        m = p ** n

        for d in meltDays:
            water = K * snowProportion[d]
	
	    # my code: shift the filter on by one day
            do something clever to shift it on by one day

            accum += m * water
        # my code: return accumulator
        return accum

This example makes it clear that significant modifications have been made to the code structure (and probably to its efficiency) although the basic model and looping comes from an existing piece of code. It clearly highlights what the actual modifications have been. Note that this is not a working example!!

Although you are supposed to do this piece of work on your own, there might be some circumstances under which someone has significantly helped you to develop the code (e.g. written the main part of it for you & you've just copied that with some minor modifications). You **must** acknowledge in your code comments if this has happened. On the whole though, this should not occur, as you **must** complete this work on your own.

If you take a piece of code from somewhere else and all you do is change the variable names and/or other cosmetic changes, you **must** acknowledge the source of the original code (with a URL if available).

Plagiarism in coding is a tricky issue. One reason for that is that often the best way to learn something like this is to find an example that someone else has written and adapt that to your purposes. Equally, if someone has written some tool/library to do what you want to do, it would generally not be worthwhile for you to write your own but to concentrate on using that to achieve something new. Even in general code writing (i.e. when not submitting it as part of your assessment) you and anyone else who ever has to read your code would find it of value to make reference to where you found the material to base what you did on. The key issue to bear in mind in this work, as it is submitted 'as your own work' is that, to avoid being accused of plagiarism and to allow a fair assessment of what you have done, you **must** clearly acknowledge which parts of it *are* your own, and the *degree to which* you could claim them to be your own.

For example, `based on ...` is absolutely fine, and you would certainly be given credit for what you have done. In many circumstances 'taken verbatim from ...' would also be fine (provided it *is* acknowledged) but then you would be given credit for what you had done with the code that you had taken from elsewhere (e.g. you find some elegant way of doing the graphs that someone has written and you make use of it for presenting your results).

The difference between what you submit here and the code you might write if this were not a piece submitted for assessment is that you the vast majority of the credit you will gain for the code will be based on the degree to which you demonstrate that you can write code to achieve the required tasks. There would obviously be some credit for taking codes from the coursenotes and bolting them together into something that achieves the overall aim: provided that worked, and you had commented it adequately and acknowledge what the extent of your efforts had been, you should be able to achieve a pass in that component of the work. If there was *no* original input other than vbolting pieces of existing code together though, you be unlikely to achieve more than a pass. If you get less than a pass in another component of the coursework, that then puts you in danger of an overall fail.

Provided you achieve the core tasks, the more original work that you do/show (that is of good quality), the higher the mark you will get. Once you have achieved the core tasks, even if you try something and don't quite achieve it, is is probably worth including, as you may get marks for what you have done (or that fact that it was a good or interesting thing to try to do).

Documentation
~~~~~~~~~~~~~

Note: All methods/functions and classes **must** be documented for the code to be adequate. Generally, this will contain:

* some text on the purpose of the method (/function/class)

* some text describing the inputs and outputs, including reference to any relevant details such as datatype, shape etc where such things are of relevance to understanding the code.

* some text on keywords, e.g.::

    def complex(real=0.0, imag=0.0):
        """Form a complex number.

        Keyword arguments:
        real -- the real part (default 0.0)
        imag -- the imaginary part (default 0.0)

        Example taken verbatim from:
	http://www.python.org/dev/peps/pep-0257/
        """
        if imag == 0.0 and real == 0.0: return complex_zero

You should look at the `document on good docstring conventions <http://www.python.org/dev/peps/pep-0257/>`_ when considering how to document methods, classes etc.

To demonstrate your documentation, you **must** include the help text generated by your code after you include the code. e.g.::

    def print_something(this,stderr=False):
        '''This does something.

        Keyword arguments:
        stderr -- set to True to print to stderr (default False)
        '''

        if stderr:
	    # import sys.stderr
            from sys import stderr

	    # print to stderr channel, converting this to str
            print >> stderr,str(this)

	    # job done, return
            return

	# print to stdout, converting this to str
        print str(this)

        return

Then the help text would be::

    Help on function print_something in module xxxx:

    print_something(this, stderr=False)
        This does something.
    
        Inputs:
        this -- an object that is printed as a string to stdout or stderr
    
        Keyword arguments:
        stderr -- set to True to print to stderr (default False)


The above example represents a 'good' level of commenting as the code broadly adheres to the style suggestions and most of the major features are covered. It is not quite 'very good/excellent' as the description of the purpose of the method (rather important) is trivial and it fails to describe the input `this` in any way. An excellent piece would do all of these things, and might well tell us about any dependencies (e.g. `requires sys if stderr set to True`).

An inadequate example would be::

    def print_something(this,stderr=False):
        '''This prints something'''
        if stderr:
            from sys import stderr
            print >> stderr,str(this)
	    return
        print str(this)

It is inadequate because it still only has a trivial description of the purpose of the method, it tells us nothing about inputs/outputs and there is no commenting inside the method. 

Word limit
~~~~~~~~~~
 
There is no word limit per se on the computer codes, though as with all writing, you should try to be succint rather than overly verbose.

Code style
~~~~~~~~~~~
A good to excellent piece of code would take into account issues raised in the `style guide <http://www.python.org/dev/peps/pep-0008/>`_. The 'degree of excellence' would depend on how well you take those points on board.


