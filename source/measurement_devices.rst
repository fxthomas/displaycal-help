Choosing a measurement device
=============================

Since DisplayCAL is all about measuring the display characteristics, we will need a measurement device.

What are we looking for?
------------------------

In order to measure our display, we need to physically measure the **brightness** of the light emitted by the display
and its **color**, when you, the user, give it any RGB value as an input. The profiles created by DisplayCAL will
contain a summarized record of these measurements.

Luckily for us, physicists and color scientists have come up with a common way of representing
these: we only need **3 values: X, Y and Z**, which together form the CIE-XYZ_ space. The
instruments in this page are all more or less accurate ways of getting these 3 values.

.. note::

   CIE-XYZ_ plays a similar central role as e.g. UTF-8 for text encoding, GMT for timezones or WGS84
   for GPS coordinates. Many (if not all) applications related to color go through CIE-XYZ as a good
   intermediate representation of colors as perceived by humans.

In general all instruments consist of:

* Something to collect light in front of the device (usually a lens)
* Something to measure light (a sensor similar to a single pixel in a camera e.g. photodiodes,...)

Colorimeters
------------

A colorimeter consists of 3 **color filters** and their associated sensors, that specifically target
the parts of the light we need to measure X, Y and Z separately.

Colorimeters generally have an advantage over other methods in terms of **price**, but also less
intuitively in terms of **speed**: you can use much bigger, and therefore less noisy sensors when
you only have 3 of them.

On the other hand, colorimeters are generally **less accurate**.

Colorimeter corrections
~~~~~~~~~~~~~~~~~~~~~~~

Examples of supported colorimeters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Spectrometers
-------------

A spectrometer is a much more complex (and expensive!) machine that can record simultaneously an
entire spectrum, sometimes measuring hundred of values inside a range of visible light wavelengths.

The output of a spectrometer is a spectrum, or a list of wavelengths and their corresponding light
intensity. The X, Y and Z values we want are then computed directly from the measured spectrum.

Usage in DisplayCAL
~~~~~~~~~~~~~~~~~~~

DisplayCAL will generally use a spectrometer in colorimeter mode, except when:

* Generating a colorimeter correction

Examples of supported spectrometers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _CIE-XYZ: https://en.wikipedia.org/wiki/CIE_1931_color_space
