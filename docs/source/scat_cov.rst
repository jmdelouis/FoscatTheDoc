scat_cov
========

.. _scat_cov

Scat_cov python class
-------------------------


.. code-block:: console
    > eval(self, image1, image2=None, mask=None, norm=None, Auto=True, calc_var=False):
     
Calculates the scattering correlations for a batch of images. Mean are done over pixels.

- mean of modulus:
  S1 = <|I * Psi_j3|>

- Normalization : take the log power spectrum:
  P00 = <|I * Psi_j3|^2>
  Normalization : take the log orig. x modulus:
- C01 = < (I * Psi)_j3 x (|I * Psi_j2| * Psi_j3)^* >
  Normalization : divide by (P00_j2 * P00_j3)^0.5
  modulus x modulus:
- C11 = <(|I * psi1| * psi3)(|I * psi2| * psi3)^*>
  Normalization : divide by (P00_j1 * P00_j2)^0.5

Parameters
----------
- image1: tensor
  Image on which we compute the scattering coefficients [Nbatch, Npix, 1, 1]
- image2: tensor
  Second image. If not None, we compute cross-scattering covariance coefficients.
- mask: [Nmask,Npix] Tensor 
- norm: None or str
  If None no normalization is applied, if 'auto' normalize by the reference P00,
      if 'self' normalize by the current P00.
  all_cross: False or True
      If False compute all the coefficient even the Imaginary part,
      If True return only the terms computable in the auto case.

Returns
-------
  S1, P00, C01, C11 normalized


