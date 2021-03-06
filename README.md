# FIR_Filter

This reposite implements a FIR filter designing for lowpass, highpass, bandpass,
bandstop. It is designed in C++. However, it is possible to use this FIR filter
as a python module. Therefore, the open-source software SWIG is used to convert
C/C++ language in script language as Python or Java. The code, a demo and an
howto can be found on https://github.com/nathanLoretan/FIR_Filter.

## Howto ##

To ease the compilation of the C++ class, a simple Makefile is created.

    $ cd /path/to/FIR_filter
    $ make

By default, the Makefile compile using python3 but it is possible to specify
the version python2.7 or python3. It is important to clean the project if the
python version is changed.

    $ make python3.5
    $ make python2.7

The makefile compiles the C++ class and create the python module. Then the python
package can be simply improted. The FIR filter class is not compiled in the
reposite.

## Demo ##

In the FIR_filter_demo.py, four FIR filters are created of each possible type.
A window function of hamming is used to improve those filters. The filters are
characterized by:
* Sampling rate: 1kHz
* Number of taps: 800
* Low pass filter cut frequency: 50Hz
* High pass filter cut frequency: 50Hz
* Band pass filter cut frequencies: 50Hz - 100Hz
* Stop band filter cut frequencies: 50Hz - 100Hz

Then, a signal composed with three frequencies, 10Hz, 75Hz and 150Hz, is created
and is filtered with the different types of FIR filter.

## API ##

`FIR_filter( int taps=0, double f1=0, double f2=0, char* type="", char* window="")`

Create an FIR_filter object.

__Parameters__

* *[in] taps    : number taps used by the filter*
* *[in] f1      : 1st cut frequency normalized*
* *[in] f2      : 2st cut frequency normalized, used only with bandstop and passband*
* *[in] type    : type of filter (lowpass, highpass, bandpass, stopband)*
* *[in] window  : window function possible (hamming, hanning, triangle, blackman)*

- - - -


`std::vector<double> getCoefficients()`

Get the coefficients calculated for the specific filter.

__Return__

*The coefficients used by the FIR filter.*

- - - -


`double filter(double new_sample)`

Filter the new sample given to the FIR filter.

__Return__

*Result of the filtering*

__Parameters__

* *[in] new_sample     : new sample*
