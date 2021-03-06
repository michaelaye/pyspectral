PySpectral
==========

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/9f039d7d640846ca89be8a78fa11e1f6)](https://www.codacy.com/app/adybbroe/pyspectral?utm_source=github.com&utm_medium=referral&utm_content=pytroll/pyspectral&utm_campaign=badger)
[![Build Status](https://travis-ci.org/pytroll/pyspectral.png?branch=develop)](https://travis-ci.org/pytroll/pyspectral)
[![Build status](https://ci.appveyor.com/api/projects/status/dgwvkldr65tyv9t2/branch/develop?svg=true)](https://ci.appveyor.com/project/adybbroe/pyspectral/branch/develop)
[![Coverage Status](https://coveralls.io/repos/github/pytroll/pyspectral/badge.svg?branch=develop)](https://coveralls.io/github/pytroll/pyspectral?branch=develop)
[![Code Health](https://landscape.io/github/pytroll/pyspectral/develop/landscape.png)](https://landscape.io/github/pytroll/pyspectral/develop)
[![PyPI version](https://badge.fury.io/py/pyspectral.svg)](https://badge.fury.io/py/pyspectral)
[![Research software impact](http://depsy.org/api/package/pypi/pyspectral/badge.svg)](http://depsy.org/package/python/pyspectral)
[![Code Climate](https://codeclimate.com/github/pytroll/pyspectral/badges/gpa.svg)](https://codeclimate.com/github/pytroll/pyspectral)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/pytroll/pyspectral/badges/quality-score.png?b=develop)](https://scrutinizer-ci.com/g/pytroll/pyspectral/?branch=develop)

Given a passive sensor on a meteorological satellite PySpectral provides the
relative spectral response (rsr) function(s) and offer you some basic
operations like convolution with the solar spectrum to derive the in band solar
flux for instance. The focus is imaging sensors like AVHRR, VIIRS, MODIS, ABI,
AHI and SEVIRI. But more sensors are included and if others are needed
they can be easily added. With PySpectral it is possible to derive the
reflective and emissive parts of the signal observed in any NIR band around 3-4
microns where both passive terrestrial emission and solar backscatter mix the
information received by the satellite. Furthermore PySpectral allows correcting
true color imagery for background (climatological) rayleigh scattering aerosol
absorption.


Adam Dybbroe
January 2018, Norrkoping, Sweden
