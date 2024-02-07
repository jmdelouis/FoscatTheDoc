Python Module Documentation
=============================

.. class:: funct
	   
   Description of the class.
   
   .. method:: __init__(NORIENT=4,
               KERNELSZ=3,
               all_type='float64',
               gpupos=0,
               TEMPLATE_PATH='data',
               BACKEND='tensorflow',
               JmaxDelta=0,
               isMPI=False,
               mpi_size=1,
               mpi_rank=0):

     Parameters
     ----------

     - ``NORIENT=4`` Number of Wavelet orientation.
     - ``KERNELSZ=3`` Size of the kernel used to define the wavelet
     - ``all_type='float64'`` Internal data format. Select ``float32`` to earn memory and speed.
     - ``gpupos=0`` Select the default GPU id if several are availble. Note that ``foscat`` always use all GPU if several losses are defined while compute synthesis.
     - ``TEMPLATE_PATH='data'`` Directory where default foscat information are stored.  
     - ``BACKEND='tensorflow'``  Select the backend. ``numpy`` and ``pytorch`` are beta testedonly.
     - ``JmaxDelta=0``  Define the delta of the last scale computed compare to the max possible scale considering the nside. For instance, the maximum number of scale usable for ``scat_cov`` of a nside=16 image is 4. ``JmaxDelta=2`` computes only the 2 first scales.
     - ``isMPI=False`` Set to ``True`` to use the inside ``MPI`` job.``mpi_size`` and ``mpi_rank`` should be set.
     - ``mpi_size=1``  Set the ``size`` of the ``MPI`` run.
     - ``mpi_rank=0`` Set the ``rank`` of the ``MPI`` run.
       
   .. method:: ud_grade(image,jscale)
	       
      return an image with a corresponding *nside* divided by a factor ``2^jscale`` compare to the input ``image`` 

   .. method:: up_grade(image,out_nside)
	       
      return an image with a corresponding *nside*=``out_nside`` using bilinear interpolation on ``image`` data.

   .. method:: convol(image,axis=0)
	       
      convol the ``image`` by default wavelet defined in ``__init__``. Input dimension is [..,Npix,..], output dimension is [..,Mpix,Norient,..]. Npix is the number of pixels of the ``image``.
      
   .. method:: smooth(image,axis=0)
	       
      smooth the ``image`` by default symetric wavelet defined in ``__init__``. Input dimension is [..,Npix,..], output dimension is [..,Mpix,..]. Npix is the number of pixels of the ``image``.

   .. method:: fill( im, nullval)

      Fill the ``im`` samples equal to ``nullval`` in such way that the ``scat_cov`` computation as less affected by unknown data. Be aware that a mask should used to get the proper statistic while doing 

   .. method:: moments( list_scat)

      Calculate the mean and the standard deviation for a list of ``scat_cov`` objects provided by ``list_scat``. The return value is ``scat_mean, scat_std``, which are two ``scat_cov`` objects representing the mean and the standard deviation values, respectively.

   .. method:: eval( image1, image2, mask, norm, Auto, calc_var)

      Calculates the scattering correlations for a batch of images. Mean are done over pixels.
      mean of modulus:
                S1 = <|I * Psi_j3|>
		Normalization : take the log
      power spectrum:
                P00 = <|I * Psi_j3|^2>
		Normalization : take the log
	orig. x modulus:
                C01 = < (I * Psi)_j3 x (|I * Psi_j2| * Psi_j3)^* >
     Normalization : divide by (P00_j2 * P00_j3)^0.5
     modulus x modulus:
                C11 = <(|I * psi1| * psi3)(|I * psi2| * psi3)^*>
     Normalization : divide by (P00_j1 * P00_j2)^0.5

     Parameters
     ----------

     - image1: tensor
       Image on which we compute the scattering coefficients [Nbatch, Npix, 1, 1]
     - image2: tensor
       Second image. If not None, we compute cross-scattering covariance coefficients.
     - mask:
     - norm: None or str
       If None no normalization is applied, if 'auto' normalize by the reference P00,
       if 'self' normalize by the current P00.
           all_cross: False or True
       If False compute all the coefficient even the Imaginary part,
       If True return only the terms computable in the auto case.
       
     Returns
     -------
     S1, P00, C01, C11 normalized
     
   .. method:: clean_norm(self)

      Internal method not to be used.

   .. method:: _compute_C01( j2, conv, vmask, M_dic, MconvPsi_dic, calc_var, return_data)

      Internal method not to be used.

   .. method:: _compute_C11( j1, j2, vmask, M1convPsi_dic, M2convPsi_dic, calc_var, return_data)

      Internal method not to be used.

   .. method:: square( x)

      Compute all coefficients (S1, P00, C01, C11, ...) attached to the ``scat_cov`` x with the square of their values.

   .. method:: sqrt( x)

      Compute all coefficients (S1, P00, C01, C11, ...) attached to the ``scat_cov`` x with the square root of their values.

   .. method:: reduce_mean( x)

      Compute the mean values of all the coefficients.

   .. method:: reduce_sum( x)

      Compute the sum values of all the coefficients.

   .. method:: ldiff( sig, x)

      Description of the method.

   .. method:: log( x)

      Compute all coefficients (S1, P00, C01, C11, ...) attached to the ``scat_cov`` x with the logarithm of their values.

   .. method:: std( list_of_sc)

      Do the standard deviation of all the coefficients

   .. method:: eval_comp_fast( image1, image2, mask, norm, Auto)

     Internal method not to be used .

   .. method:: eval_fast( image1, image2, mask, norm, Auto)

     Same method than ``eval`` but run in Graph Execution mode fastest while doing lot of eval_fast. The first execution could be long.

   .. method:: backend.bk_real(x)

      return the real part of the ``x`` data.

   .. method:: backend.bk_conjugate(x)

      return the conjugate value of the ``x`` data.

   .. method:: backend.bk_norm(x)

      return the complex norm value of the ``x`` data.


.. class:: scat_cov

   Description of the class.

   .. method:: __init__( s0, p00, c01, c11, s1, c10, backend)

      Description of the method.

   .. method:: numpy(self)

      Description of the method.

   .. method:: constant(self)

      Description of the method.

   .. method:: flatten(self)

      Description of the method.

   .. method:: flattenMask(self)

      Description of the method.

   .. method:: get_S0(self)

      Description of the method.

   .. method:: get_S1(self)

      Description of the method.

   .. method:: get_P00(self)

      Description of the method.

   .. method:: reset_P00(self)

      Description of the method.

   .. method:: get_C01(self)

      Description of the method.

   .. method:: get_C10(self)

      Description of the method.

   .. method:: get_C11(self)

      Description of the method.

   .. method:: get_j_idx(self)

      Description of the method.

   .. method:: get_jc11_idx(self)

      Description of the method.

   .. method:: __add__( other)

      Description of the method.

   .. method:: relu(self)

      Description of the method.

   .. method:: __radd__( other)

      Description of the method.

   .. method:: __truediv__( other)

      Description of the method.

   .. method:: __rtruediv__( other)

      Description of the method.

   .. method:: __rsub__( other)

      Description of the method.

   .. method:: __sub__( other)

      Description of the method.

   .. method:: domult( x, y)

      Description of the method.

   .. method:: dodiv( x, y)

      Description of the method.

   .. method:: domin( x, y)

      Description of the method.

   .. method:: doadd( x, y)

      Description of the method.

   .. method:: __mul__( other)

      Description of the method.

   .. method:: __rmul__( other)

      Description of the method.

   .. method:: interp( nscale, extend, constant)

      Description of the method.

   .. method:: plot( name, hold, color, lw, legend)

      Description of the method.

   .. method:: get_np( x)

      Description of the method.

   .. method:: save( filename)

      Description of the method.

   .. method:: read( filename)

      Description of the method.

   .. method:: std(self)

      Description of the method.

   .. method:: mean(self)

      Description of the method.

   .. method:: initdx( norient)

      Description of the method.

   .. method:: sqrt(self)

      Description of the method.

   .. method:: L1(self)

      Description of the method.

   .. method:: square_comp(self)

      Description of the method.

   .. method:: iso_mean( repeat)

      Description of the method.

   .. method:: fft_ang( nharm)

      Description of the method.

   .. method:: iso_std( repeat)

      Description of the method.

   .. method:: get_nscale(self)

      Description of the method.

   .. method:: get_norient(self)

      Description of the method.

   .. method:: add_data_from_log_slope( y, n, ds)

      Description of the method.

   .. method:: add_data_from_slope( y, n, ds)

      Description of the method.

   .. method:: up_grade( nscale, ds)

      Description of the method.
	      
