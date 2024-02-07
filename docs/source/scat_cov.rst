
scat_cov Module
===============

This module defines the ``scat_cov`` class and related functions.

Functions
---------

.. function:: read(filename)

   Reads data from the specified file and returns a ``scat_cov`` object.

   :param filename: The name of the file to read from.
   :type filename: str
   :returns: A ``scat_cov`` object initialized with data from the file.

scat_cov Class
--------------

.. class:: scat_cov(s0, p00, c01, c11, s1=None, c10=None, backend=None)

   Represents a scatter covariance object with attributes and methods for managing scatter covariance data.

   :param s0: Description of `s0`.
   :param p00: Description of `p00`.
   :param c01: Description of `c01`.
   :param c11: Description of `c11`.
   :param s1: Description of `s1`. Optional.
   :param c10: Description of `c10`. Optional.
   :param backend: Description of the backend. Optional.

   .. method:: __init__(s0, p00, c01, c11, s1=None, c10=None, backend=None)

      Initializes a new instance of the ``scat_cov`` class.

   .. method:: numpy()

      Converts the attributes to numpy arrays and returns a new ``scat_cov`` object with these numpy arrays.

