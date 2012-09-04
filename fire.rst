Fire/ENSO teleconnections
=========================

.. image:: http://www.geog.ucl.ac.uk/images/admissions/pg/rs/kruger_post_fire.jpg

Introduction
------------

There is much public and scientific interest in monitoring and predicting the activity of wildfires and such topics are `often in the media <http://www.bbc.co.uk/news/science-environment-15691060>`_.

Part of this interest stems from the role fire plays in issues such as `land cover change, deforestation and forest degradation <http://www.eufirelab.org/toolbox2/library/upload/2086.pdf>`_  and `Carbon emissions <http://www.google.com/url?sa=t&rct=j&q=fire%20carbon%20emissions&source=web&cd=6&ved=0CFEQFjAF&url=http%3A%2F%2Fwww.kcl.ac.uk%2Fsspp%2Fdepartments%2Fgeography%2Fpeople%2Facademic%2Fwooster%2F30yongwoosteretal.pdf&ei=4FPCTuvZE9Gg8gPZybyxBA&usg=AFQjCNG81fTRoCcK1nhKnk3u0b8az24bGQ&sig2=EjJYm2S-_2gHu2vgt4ByvA&cad=rja>`_ from the land surface to the atmosphere, but also of concern are `human health impacts <http://www.fire.uni-freiburg.de/iffn/country/id/id_32.htm>`_. The impacts of fire should not however be considered as wholy negative, as it plays a `significant role in natural ecosystem processes <http://www.fl-dof.com/publications/fires_natural_role.html#firerole>`_.

For many regions of the Earth, there are large inter-annual variations in the timing, frequency and severity of wildfires. Whilst anthropogenic activity accounts for a `large and probably increasing proportion of fires started <http://www.google.com/url?sa=t&rct=j&q=fire%20frequency%20july%204th&source=web&cd=7&ved=0CFIQFjAG&url=http%3A%2F%2Farctic.synergiesprairies.ca%2Farctic%2Findex.php%2Farctic%2Farticle%2Fdownload%2F2806%2F2783&ei=K1bCTqv1MYS28QOR9ekG&usg=AFQjCNFKillAOZMXrT5xpFhckMKvqW50Vg&sig2=r3J6454VcvI1xpC3Sf3RKw&cad=rja>`_, this is not in itself `a new phenomenon <http://www.google.com/url?sa=t&rct=j&q=anthropogenic%20fire&source=web&cd=2&ved=0CCcQFjAB&url=http%3A%2F%2Fwww.as.ua.edu%2Fant%2Fbindon%2Fant475%2FPapers%2FHamm.pdf&ei=rFXCTu-PHsay8QPdy-2MBA&usg=AFQjCNGUMrfnDTwRDBxFB-wioZokBt8EtA&sig2=Zt1nfHoKktbka-pEZs6NGw&cad=rja>`_.

Fires spread where: (i) there is an ignition source (lightning or man, mostly); (ii) sufficient combustible fuel to maintain the fire. The latter is strongly dependent on fuel loads and mositure content, as well as meteorological conditions. Generally then, when conditions are drier (and there is sufficient fuel and appropriate weather conditions), we would expect fire spread to increase. If the number of ignitions remained approximately constant, this would mean more fires. 
`Many models of fire activity <http://www.nasa.gov/images/content/492949main_Figure-2-Wildfires.jpg>`_ predict increases in fire frequency in the coming decades, although there may well be `different behaviours in differet parts of the world <http://news.sciencemag.org/sciencenow/2009/04/10-02.html>`_.

.. image:: images/492949main_Figure-2-Wildfires.jpg
   :scale: 40%
   :target: http://www.nasa.gov/images/content/492949main_Figure-2-Wildfires.jpg

Satellite data has been able to provide us with increasingly useful tools for monitoring wildfire activity, particularly since 2000 with the MODIS instruments on the NASA Terra and Aqua (2002) satellites. A suite of `'fire' products <http://modis-fire.umd.edu/index.html>`_ have been generated from these data that have been used in a large number of `publications <http://modis-fire.umd.edu/Publications.html>`_ and `practical/management <http://maps.geog.umd.edu/firms/#>`_ projects.

There is growing evidence of 'teleconnection' links between fire occurence and large scale climate patterns, such as `ENSO <http://www.esrl.noaa.gov/psd/enso/>`_.

.. image:: images/ts.png

The proposed mechanisms are essentially that such climatic patterns are linked to local water status and temperature and thus affect the ability of fires to spread. For some regions of the Earth, empirical models built from such considerations have quite reasonable predictive skill, meaning that fire season severity might be `predicted some months ahead of time <http://www.sciencemag.org/content/334/6057/787.full>`_.


A Practical  Exercise
---------------------

In this session
~~~~~~~~~~~~~~~

In this session, you will be working in groups (of 3 or 4) to build a computer code in python to explore links between fire activity and Sea Surface Temperature anomalies.

This is a team exercise, but does not form part of your formal assessment for this course. You should be able to complete the exercise in the 3 hour session, if you work effectively as a team. Staff will be on hand to provide pointers. 

You should be able to complete the exercise using coding skills and python modules that you have previously experience of, though we will also provide some pointers to get you started.


Statement of the problem
~~~~~~~~~~~~~~~~~~~~~~~~

Using monthly fire count data from MODIS Terra, develop and test a predictive model for the number of fires per unit area per year driven by Sea Surface Temperature anomaly data.

Datasets
~~~~~~~~

We suggest that the datasets you use of this analysis, following `Chen at al. (2011) <http://www.sciencemag.org/content/334/6057/787.full>`_, are:

* MODIS Terra fire counts (2001-2011) (`MOD14CMH <http://www.google.com/url?sa=t&rct=j&q=mod14cmh&source=web&cd=1&ved=0CBwQFjAA&url=http%3A%2F%2Fmodis-fire.umd.edu%2FDocuments%2FMODIS_Fire_Users_Guide_2.4.pdf&ei=QWXCTuHQDdGq8AOziOmyBA&usg=AFQjCNE1qq9B1RH28AcYMisWnAhZsWKL_A&sig2=5DYBhzuCIA6lWg9lp1oNww&cad=rja>`_). The particular dataset you will want from the file is 'SUBDATASET_2 [360x720] CloudCorrFirePix (16-bit integer)'.
* Climate index data from `NOAA <http://www.esrl.noaa.gov/psd/data/climateindices/list/>`_

If you ever wish to take this study further, you can find various other useful datasets such as `these <https://webfiles.uci.edu/ychen17/www/research_datamap.html>`_.

The MOD14CMH `CMG data <http://maps.geog.umd.edu/firms/CMG.htm>`_  are available from the `UMD ftp server <ftp://fire:burnt@fuoco.geog.umd.edu/modis/C5/cmg/monthly/hdf>`_ but the data you will need are also directly available from `/data/geospatial_10/ucfajlg/MOD14CMH/ <http://www.geog.ucl.ac.uk/~plewis/geogg122/MOD14CMH>`_. Note that, if you are on the UCL system, you do not need to *copy* the data, just use them from where they are.

The data are HDF format, so you should know how to `read them into a numpy array in python <http://www2.geog.ucl.ac.uk/~plewis/geogg122/readhdf.html#read-an-hdf-file-e-g-modis-data-products>`_.


Some suggestions
~~~~~~~~~~~~~~~~

It is suggested that, again following `Chen at al. (2011) <http://www.sciencemag.org/content/334/6057/787.full>`_, you develop the empirical models at a resolution of 5 degrees by 5 degrees. 

You may also wish to limit the geographical extent of your analysis (e.g. continental).

We would suggest that you break the problem down into sub-problems so that you can make best use of your team. One way to do this would be:

* code to generate fire datasets
* code to perform correlation analysis
* code to perform prediction
* documentation

Below, we will provide some pointers for each of these tasks. We will also provide code that will perform the tasks, but you should only use this if you are completely stuck, and only then to get some idea how to proceed.

code to generate fire datasets
------------------------------

inputs and outputs
~~~~~~~~~~~~~~~~~~

First, you need to think about what your inputs and outputs are.

The inputs are the set of hdf files::

    import glob
    datadir = '/data/geospatial_10/ucfajlg/MOD14CMH/'
    files = sorted(glob.glob(datadir+'/*.hdf'))
    
The outputs will be a set of NY size (36,72) datasets, where NY is the number of years for which you have data (2001 to 2010) representing:

* total number of fires
* the month on maximum fire activity

required functions
~~~~~~~~~~~~~~~~~~

To get from the inputs to the outputs, you will need to define a set of steps to go through. You could phrase these as methods, so you can easily piece them together into the required code.

One set of example methods could be:

* **shrink**: inputs: array of size (360,720); outputs: array of size (36,72). The purpose of this would be to take in the fire count array at the native 0.5 degree resolution, and return the fire count at 5 degree resolution. Essentially, it involves summing up the fire counts in each 10x10 pixels.

* **get_data**: inputs: list of filenames for a particular year; outputs: array of 12 x (360,720) (i.e. one dataset for each month of the year) fire count values. This method could simply be a loop over each of the filenames to use e.g. gdal to open the specified hdf file and pull out the required dataset and add these data to an array to return. You should note that 'no data' is set to -1 in this dataset, so as soon as you pull the data, you would probably want to set all negative values to zero. You might also consider calling your **shrink** method whilst in this loop, in which case you could return and array of size 12 x (36,72)

* **get_max_fire**: inputs: data array of 12 x (36,72) which is the 5 degree by 5 degree version of the fire counts for a particular year; outputs: an array containing the total number of fires over the year per pixel (size (36,72)) *and* an array containing the month the maximum number of fires occurred (the peak fire month). You could split this into two methods. The first part, total number of fires, is straightforward (hint: see the `axis` option for `numpy.sum() <http://docs.scipy.org/doc/numpy/reference/generated/numpy.sum.html>`_). The second part is slightly trickier. You would need to find the maximum value of the fire count for each pixel (quite similar to getting total number of fires) then find which month matched this. You would probably find it easiest to loop over each pixel individually to achieve that. You could, if you flet confident, combine **get_max_fire** and **get_data** into a single method.

* **get_month_year**: at some point in your code, it is likely that you will need to know the year associated with a particular MODIS filename. You can easily do that using `split() <http://docs.python.org/library/stdtypes.html#str.split>`_ operations on the filename, but you might like to write a particular method to do this for a list of filenames.

* **plotting**: it is probably agood idea to set up a plotting method using pylab. This could, for example, plot the firecount data in an upper panel and the month of maximum fire in a lower panel, for a particular year. The output then might look something like:

.. image:: fireplot_2010.png

* **putting it all together**: To achieve the aim of this part of the code, you would need to: get a list of the filenames (ideally, sorted as it would make lfe easier later); work out the year associated with each filename; loop over each year that you want to process, and get the fire count and peak fire month dataset; return all of the fire count and peak fire month data. You could of course structure it differently, but that is probably the most straightforward approach. You might find it useful to save the dataset that you generate (rather than just returning it). You would generally use `numpy.savez() <http://docs.scipy.org/doc/numpy/reference/generated/numpy.savez.html>`_ for that (check the help page on how to use that: use `np.load() <http://docs.scipy.org/doc/numpy/reference/generated/numpy.load.html>`_ to reaload it later).


If you hit **major** problems, then a piece of code that does all of these tasks in pretty much the way described is given `here <python/fire.py>`_, though it is rather defeating the purpose of the exercise to go there. Alternatively, if you are really stuck on this part of the work (or want to prototype code for other parts of the task), you can load a file `firedata.npz <python/firedata.npz>`_. To use this::

    import numpy as np
    data = np.load('firedata.npz')
    years = data['arr_1']
    firecount = data['arr_0'][:,0,:,:]
    firemonth = data['arr_0'][:,1,:,:]

To visualise this then e.g. for 2009::

    import pylab
    eg_year = 2009
    i = np.where(years == eg_year)[0][0]
    pylab.subplot(2,1,1)
    pylab.imshow(firecount[i,:,:],interpolation='nearest')
    pylab.subplot(2,1,2)
    pylab.imshow(firemonth[i,:,:],interpolation='nearest')

.. image:: fireplot_2009.png

Note that in the firemonth dataset here, month 1 is January.

code to perform correlation analysis
------------------------------------

The idea here is, for a particular (or set of) SST anomaly measures, which 'lag' month gives the highest correlation coefficient with fire count. By 'lag' month, we mean that e.g. if the peak fire month for a particular pixel was September, which month prior to that has a set of SST anomalies over the sample years that is most strongly correlated with fire count. So, if we were using a single SST anomaly measure (e.g. `AMO <http://www.esrl.noaa.gov/psd/data/correlation/amon.us.data>`_ or `ONI <http://www.esrl.noaa.gov/psd/data/correlation/oni.data>`_) and sample years 2001 to 2009 to build our model, then we would do a linear regression of fire count for a particular pixel over these years against e.g. AMO data for September (lag 0) then August (lag 1) then July (lag 2) etc. and see which produced the highest R^2.

So first, download the SST anomaly data you want, e.g. `AMO <http://www.esrl.noaa.gov/psd/data/correlation/amon.us.data>`_ in `amon.us.data <amon.us.data>`_.

The `file <amon.us.data>`_ has header and tail lines, that we can quite easily deal with, but you might find it easiest to simply copy the file to e.g. `amon.us.dat <amon.us.dat>`_ and comment out the first and last three lines with a # character. Then, you can easily read the data in with `numpy.loadtxt() <http://docs.scipy.org/doc/numpy/reference/generated/numpy.loadtxt.html>`_::

    import numpy as np
    amo_data = np.loadtxt('amon.us.dat')
    amo_years = amo_data[:,0].astype(int)
    amo =  amo_data[:,1:]

so now we have the years of the dataset stored in `amo_years` and the dataset (shape (64, 12)) in the variable `amo`.

Lets assume that the years of data that we want to process are 2001-2009 inclusive::

    y = np.arange(2001,2010)
    which_amo_years = np.in1d(amo_years,y)
    amo_sub = amo[which_amo_years,:]

where we have used the numpy method `np.in1d <http://docs.scipy.org/doc/numpy/reference/generated/numpy.in1d.html>`_ to filter out which elements of the dataset we want. The partial dataset then, covering the years we want, is `amo_sub`, which is of shape (9,12) i.e. 9 years, 12 months.

f we thought the problem through, we might at this point foresee a potential problem when we are trying to get AMO data for e.g. lag 10 months for a peak fire month of January (month 1). In that case, we would need AMO data from the previous year, which we don't currently have. A solution to that would be to pull out another dataset, for the years `y-1` (i.e. 2000-2008 inclusive) and combine that with `amo_sub`::

    amo_sub_prev = amo[np.in1d(amo_years,y-1),:] 
    big_amo = np.hstack((amo_sub_prev, amo_sub))

This can be done with the numpy method `numpy.hstack() <http://docs.scipy.org/doc/numpy/reference/generated/numpy.hstack.html>`_, where the new array, `big_amo` is now of shape (9, 24). So, if we want amo data for month 9 (September), we now need to add 11 (12, minus 1 since here, the month is one-based)::

    amo_sept = big_amo[:,9+11]

which we can verify from the original file `amon.us.data <amon.us.data>`_ is correct for the years 2001-2009 inclusive.

Similarly, for lag 11 months from September then, we have::

    amo_sept_lag11 = big_amo[:,9+11-11]

which we can also check from the original data. That is a bit of an unwanted complexity, but is a simple enough way around the problem.

Lets now assume that you will do the analysis for a single pixel. If you read the fire data from the file `firedata.npz <python/firedata.npz>`_ as above, then pull out a pixel e.g. (27,20) (in South America)::

    import numpy as np
    data = np.load('firedata.npz')
    years = data['arr_1']
    firecount = data['arr_0'][:,0,:,:]
    firemonth = data['arr_0'][:,1,:,:].astype(int)
    which_y = np.in1d(years,y) 
    fc = firecount[which_y,20,27]
    fm = firemonth[which_y,20,27]


If we look at the variable `fm` we will note that the peak fire month can vary from year to year. Unless we specifically want to predict the peak fire month in our model, we might greatly simplify the analysis by taking a constant value over all years. A sensible choice for this might be the median value::

    mfiremonth = np.median(firemonth,axis=0)
    fm = mfiremonth[20,27]

We are now in a position to be able to look at the relationship betwen fire count (for this pixel) for the years 2001-2009 and amo. At lag 0 then::

    import pylab
    lag = 0
    x = big_amo[:,fm+11-lag]
    y = fc
    coeffs = np.polyfit(x, y, 1)
    m = coeffs[0]
    c = coeffs[1]
    correlation = np.corrcoef(x, y)[0,1]
    pylab.plot(x,y,'ro')
    pylab.plot(x,m*x+c)
    pylab.title('pixel (20,27) lag %d: r = %.2f'%(lag,correlation))
    pylab.savefig('firecount.png')
    

.. image:: images/firecount.png

Or, if we wanted to loop over lags 0 to 11 (inclusive) and calculate r::

    y = fc
    rs = []
    for lag in np.arange(12):
        x = big_amo[:,fm+11-lag]
        rs.append(np.corrcoef(x, y)[0,1])
     r2 = np.array(rs * rs) 
     lag_max_r2 = np.where(r2 == np.max(r2))[0][0]
     lag = lag_max_r2
     max_r2 = r2[lag]
     x = big_amo[:,fm+11-lag]
     coeffs = np.polyfit(x, y, 1)
     m = coeffs[0]
     c = coeffs[1]

So, the largest R2 is obtained here at a lag of 2 months, but the value is only 0.293.

.. image:: images/firecount2.png

This is not a particularly strong relationship, but it could be that for this pixel, the relationship is stronger with other SST anomalies.

Developing a computer code
~~~~~~~~~~~~~~~~~~~~~~~~~~

In the example above, we have taken you through the steps that you would need to go through to find the maximum R2 and the linear regression coefficients (m and c) for a particular pixel. To achieve the aim of this exercise, you need to produce spatial datasets of R2 (for the world or specific regions), along with the associated data on the 'best' lag for each pixel, and the regression coefficients.

You should run this code on several SSI anomaly datasets, at the very least ONA and AMO.

You need to save the spatial dataset to a file when you have calculated it, which you can achieve with `numpy.savez() <http://docs.scipy.org/doc/numpy/reference/generated/numpy.savez.html>`_.

To complete the exercise, you should combine results from different SSI anomalies to give the 'best' (in an R2 sense) model for each pixel.

You have most of the ideas above that you will need to do this, but in case you are really stuck, an example code is provided  `here <python/fire2.py>`_.

You results should probably look similar to (for AMO):

.. image:: images/ssi_rs.png

.. image:: images/ssi_rl.png

.. image:: images/ssi_rm.png

.. image:: images/ssi_rc.png
 
Unsurprisingly, these results are similar to those obtained by `Chen et al. (2011) <http://www.sciencemag.org/content/334/6057/787.full>`_, although they considered only the maiximum positive correlation. Their results are shown:

.. image:: images/anom.png  

with the results for AMO R2 shown on the right.

A saved version of the dataset is available in the file `firestats.npz <python/firestats.npz>`_. To decode this::

    import numpy as np
    data = np.load('firestats.npz')
    c = data['c']
    m = data['m']
    lag = data['lag']
    max_r2 = data['max_r2']

code to perform prediction
--------------------------

We can assume for this code that a file such as `firestats.npz <python/firestats.npz>`_ has been created, and this can be read in as above::

    import numpy as np
    data = np.load('firestats.npz')
    c = data['c']
    m = data['m']
    lag = data['lag']
    max_r2 = data['max_r2']

we will also assume that some methods from the above problem are available (in the file `fire3.py <python/fire3.py>`_::

    from fire3 import get_ssi,firedata
    
We assume the files `firedata.npz <http://www2.geog.ucl.ac.uk/~plewis/geogg122/python/firedata.npz>`_ and `amon.us.dat <http://www2.geog.ucl.ac.uk/~plewis/geogg122/amon.us.dat>`_ are also available, so we can load data for the year 2010::

    y = np.array([2010])
    ssi = get_ssi(y,'amon.us.dat')[0]
    fc,fm = firedata(y,'firedata.npz')

We need to get the SSI data for the particular lags used::

    actual_lag = (fm + 11 - lag).astype(int)
    X = np.zeros_like(fm).astype(float)
    for i in xrange(24):
        ww = np.where(actual_lag == i)
        X[ww] = ssi[i]
    

All we have to do now, is to perform a prediction of Y from the model Y = m X + c, with X.

The result may be something like:

.. image:: images/firepred.png

where the upper panel is the model prediction and the low panel the observations.

Or, as a scatterplot:

.. image:: images/firepredscatter.png

which is quite an interesting result...

Documentation
-------------

If you have spare time or resources in your group, you might find it of interest to write up some documentation for the code you develop. Probably the best way to do that would be to use `sphinx <http://sphinx.pocoo.org/>`_.

To get started with that, you can type::

    berlin% sphinx-quickstart

and follow the instructions. That will produce a file called `index.rst <source/index.rst>`_ that you can modify to include `rst format <http://sphinx.pocoo.org/rest.html>`_ text, images, equations etc. We leave it for you to explore!

Summary
-------

This session has been a team effort at building a piece of code to conduct a scientific experiment in a three hour session. 
