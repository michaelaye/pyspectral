Installation
------------

PySpectral reads relative spectral response functions for various satellite
sensors. The original agency specific spectral response data are stored in
various formats (e.g. ascii, excel, or netCDF) and usually not following any
agreed international standard. These data are usually available at the
satellite agencies responsible for the instrument in question. That is for
example EUMETSAT, NOAA, NASA, JMA and CMA. The Global Space-based
Inter-Calibration System (GSICS_) Coordination Center (GCC_) holds a place with
links to several relevant `instrument response data`_. But far from all data
are available through that web-site.


The spectral response data 
^^^^^^^^^^^^^^^^^^^^^^^^^^

So all these instrument relative spectral response data are stored in different
formats with varying levels of detailed information available. Therefore, in
order to make life easier for the *PySpectral* user we have defined one common
internal hdf5 format. That way it is also easy to add support for new
instruments. Currently the relative spectral reponses for Suomi-NPP VIIRS, all
of the NOAA/TIROS-N and Metop AVHRRs, Terra/Aqua MODIS, Meteosat 8-11 SEVIRI,
Sentinel-3A SLSTR and OLCI, Envisat AATSR, GOES-16 ABI, and Himawari-8 are
available. The data are automagically downloaded and installed when needed. But
if you need to specifically retrieve the data independently the data are
available from the `pyspectral rsr`_ repository. (The md5sum of this gzipped
tar file is bc36ffad302cdce66c6796b251607d1c).

It is still also possible to download the original spectral responses from the
various satellite operators instead and generate the internal hdf5 formatet
files yourself. However, this should normaly never be needed. For SEVIRI on
Meteosat download the data from eumetsat_ and unzip the Excel file.


Installation
^^^^^^^^^^^^

Installation of the latest stable version is always done using:: 

  $>  pip install pyspectral

Some static data are part of the package but both the Rayleigh correction
coefficients and the spectral responses are downloaded and installed once
PySpectral is being run the first time. On default these static data will
reside in the platform specific standard destination for storing user data,
via the use of the appdirs_ package.
On Linux this will be under *~/.local/share/pyspectral*. See further down.

You can also choose to download the PySpectral source code from github_::

  $> git clone git://github.com/pytroll/pyspectral.git

and then run::

  $> python setup.py install

or, if you want to hack the package::

  $> python setup.py develop


Configuration file
^^^^^^^^^^^^^^^^^^

A default configuration file *pyspectral.yaml* is installed automatically and
being part of the package under the *etc* directory. In many cases the default
settings will allow one to do all what is needed. However, it can easily be
overwritten by making your own copy and set an environment variable pointing to
this configuration file, as e.g.::

  $> PSP_CONFIG_FILE=/home/a000680/pyspectral.yaml; export PSP_CONFIG_FILE

So, in case you want to download the internal PySpectral formatet relative
spectral responses as well as the rayleigh-correction look-up-tables once and
for all, and keep them somewhere else, here is what you need to do::

  $> cd /path/to/internal/rsr_data
  $> wget https://zenodo.org/record/1012412/files/pyspectral_rsr_data.tgz
  $> tar xvzf pyspectral_rsr_data.tgz

  $> cd /path/to/rayleigh/correction/luts
  $> mkdir rural_aerosol rayleigh_only
  $> cd rayleigh_only/
  $> wget https://zenodo.org/record/888971/files/pyspectral_rayleigh_correction_luts.tgz
  $> tar xvzf pyspectral_rayleigh_correction_luts.tgz
  $> cd ../rural_aerosol
  $> wget https://zenodo.org/record/896881/files/pyspectral_rayleigh_correction_luts.tgz
  $> tar xvzf pyspectral_rayleigh_correction_luts.tgz

Then adjust the *pyspectral.yaml* so it looks something like this:

.. code-block:: ini

   rsr_dir = /path/to/internal/rsr_data
   rayleigh_dir = /path/to/rayleigh/correction/luts
   download_from_internet = False


.. _pyspectral rsr: https://zenodo.org/record/1012412/files/pyspectral_rsr_data.tgz
.. _eumetsat: http://www.eumetsat.int/website/wcm/idc/idcplg?IdcService=GET_FILE&dDocName=ZIP_MSG_SEVIRI_SPEC_RES_CHAR&RevisionSelectionMethod=LatestReleased&Rendition=Web
.. _GSICS: http://www.wmo.int/pages/prog/sat/GSICS/
.. _GCC: http://www.star.nesdis.noaa.gov/smcd/GCC/index.php
.. _instrument response data: http://www.star.nesdis.noaa.gov/smcd/GCC/instrInfo-srf.php
.. _github: http://github.com/pytroll/pyspectral
.. _appdirs: https://github.com/ActiveState/appdirs
