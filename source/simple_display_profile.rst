Generating a simple display profile
===================================

Usage
-----

The goal of this first guide is to get a basic calibration and profile for a
single display that is suitable for most use cases, in particular editing
images intended to be viewed on websites.

* **Display white point** is set to D65_ (6500K) for all applications,
  regargless of their support of color management and display profiles.
* **Luminance curve** is set to the sRGB_ tone curve for all applications,
  regardless of their support of color management and display profiles.
* **Color rendering** of RGB values approximately corresponds to the sRGB_
  space in applications that are not fully color-managed, only fully
  color-managed applications will render colors accurately.

Required hardware
-----------------

* A colorimeter
* A computer running Linux or Windows
* A display with at least 100% sRGB coverage

Instructions
------------

Verification
------------

.. _D65: https://en.wikipedia.org/wiki/Illuminant_D65
.. _sRGB: https://en.wikipedia.org/wiki/SRGB
