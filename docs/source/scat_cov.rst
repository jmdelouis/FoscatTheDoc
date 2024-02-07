Python Module Documentation
=============================

.. class:: scat_cov

   Description of the class.

   .. method:: __init__(self, s0, p00, c01, c11, s1, c10, backend)

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

   .. method:: __add__(self, other)

      Description of the method.

   .. method:: relu(self)

      Description of the method.

   .. method:: __radd__(self, other)

      Description of the method.

   .. method:: __truediv__(self, other)

      Description of the method.

   .. method:: __rtruediv__(self, other)

      Description of the method.

   .. method:: __rsub__(self, other)

      Description of the method.

   .. method:: __sub__(self, other)

      Description of the method.

   .. method:: domult(self, x, y)

      Description of the method.

   .. method:: dodiv(self, x, y)

      Description of the method.

   .. method:: domin(self, x, y)

      Description of the method.

   .. method:: doadd(self, x, y)

      Description of the method.

   .. method:: __mul__(self, other)

      Description of the method.

   .. method:: __rmul__(self, other)

      Description of the method.

   .. method:: interp(self, nscale, extend, constant)

      Description of the method.

   .. method:: plot(self, name, hold, color, lw, legend)

      Description of the method.

   .. method:: get_np(self, x)

      Description of the method.

   .. method:: save(self, filename)

      Description of the method.

   .. method:: read(self, filename)

      Description of the method.

   .. method:: std(self)

      Description of the method.

   .. method:: mean(self)

      Description of the method.

   .. method:: initdx(self, norient)

      Description of the method.

   .. method:: sqrt(self)

      Description of the method.

   .. method:: L1(self)

      Description of the method.

   .. method:: square_comp(self)

      Description of the method.

   .. method:: iso_mean(self, repeat)

      Description of the method.

   .. method:: fft_ang(self, nharm)

      Description of the method.

   .. method:: iso_std(self, repeat)

      Description of the method.

   .. method:: get_nscale(self)

      Description of the method.

   .. method:: get_norient(self)

      Description of the method.

   .. method:: add_data_from_log_slope(self, y, n, ds)

      Description of the method.

   .. method:: add_data_from_slope(self, y, n, ds)

      Description of the method.

   .. method:: up_grade(self, nscale, ds)

      Description of the method.

.. class:: funct

   Description of the class.

   .. method:: fill(self, im, nullval)

      Fill the ``im`` samples equal to ``nullval`` in such way that the ``scat_cov`` computation as less affected by unknown data. Be aware that a mask should used to get the proper statistic while doing 

   .. method:: moments(self, list_scat)

      Calculate the mean and the standard deviation for a list of ``scat_cov`` objects provided by ``list_scat``. The return value is ``scat_mean, scat_std``, which are two ``scat_cov`` objects representing the mean and the standard deviation values, respectively.

   .. method:: eval(self, image1, image2, mask, norm, Auto, calc_var)

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

      Description of the method.

   .. method:: _compute_C01(self, j2, conv, vmask, M_dic, MconvPsi_dic, calc_var, return_data)

      Internal method not to be used.

   .. method:: _compute_C11(self, j1, j2, vmask, M1convPsi_dic, M2convPsi_dic, calc_var, return_data)

      Internal method not to be used.

   .. method:: square(self, x)

      Compute all coefficients (S1, P00, C01, C11, ...) attached to the ``scat_cov`` x with the square of their values.

   .. method:: sqrt(self, x)

      Compute all coefficients (S1, P00, C01, C11, ...) attached to the ``scat_cov`` x with the square root of their values.

   .. method:: reduce_mean(self, x)

      Compute the mean values of all the coefficients.

   .. method:: reduce_sum(self, x)

      Compute the sum values of all the coefficients.

   .. method:: ldiff(self, sig, x)

      Description of the method.

   .. method:: log(self, x)

      Compute all coefficients (S1, P00, C01, C11, ...) attached to the ``scat_cov`` x with the logarithm of their values.

   .. method:: std(self, list_of_sc)

      Do the standard deviation of all the coefficients

   .. method:: eval_comp_fast(self, image1, image2, mask, norm, Auto)

     Internal method not to be used .

   .. method:: eval_fast(self, image1, image2, mask, norm, Auto)

     Same method than ``eval`` but run in Graph Execution mode fastest while doing lot of eval_fast. The first execution could be long.

