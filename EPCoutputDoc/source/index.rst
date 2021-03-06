.. EPCoutput documentation master file, created by
   sphinx-quickstart on Mon Dec 10 15:03:15 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

How to output the electron-phonon matrix element using this extension
======================================================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

This version of Quantum-Espresso includes small extension to output 
the electron-phonon matrix element into the file named "elphmat.dat".

The most of codes in this version inherits the sample code provided at
	http://epw.org.uk/Documentation/School2018
	Hands-on 2: Electron-phonon coupling in QE --> Tues.5.tar and Extra

The above version of code only output the electron-phonon matrix element at Gamma point (for k) to standard output.
Thus, I modify several part in PHonon package in Quantum-Espresso to output the matrix element on electron k-point 
or specific single k-point.

usage
==================
If you want to output the matrix element at all k-points (for electron)
using the following tags in the input for ph.x 

::

	electron_phonon ='simple'
	elphout_all =.true.

If you want the matrix element on specific k-point
using the following tags in the input for ph.x

::

	electron_phonon ='simple'
	elphout_all =.false.
	elphout_k = 4
 
The integer index of elphout_k corresponds to the index of irreducible k-points in ph.x calculation.
To help setting this tag, I also output the coordinates of the irreducible k-points in the standard output 
as the followings

::

	number of total irreducible total k-points:          19
	k-points information:
	xk   0.000000  0.000000  0.000000
	xk   0.000000  0.096225  0.000000
	xk   0.000000  0.192450  0.000000
	xk   0.000000  0.288675  0.000000


attention
==================
In order to gather all k-point information, -npool option should be 1 when running ph.x.
For example

::

	ph.x -npool 1 < graphene.phonon.in > phonon.out 


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
