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

.. note::

   For the curious, `X-Rite i1 Display PRO teardown <https://www.youtube.com/watch\?v\=QAwKOGSow-s>`_ shows the
   various filters inside a very common colorimeter that is well-supported by DisplayCAL. `This page
   <https://displaycalibrations.com/x-rite_i1_measurement_solutions_info.html>`_ contain more technical information
   about the technical specifications of this specific model.

Colorimeters generally have an advantage over other methods in terms of **price**, but also less
intuitively in terms of **speed** (notably over spectrometers): you can use much bigger, and
therefore less noisy sensors when you only have 3 of them.

The biggest disadvantage of colorimeters is their **accuracy** if not enough care is given, since
their filters never perfectly match CIE-XYZ. They're generally provided with a factory correction to
compensate for that.

.. note::

Colorimeter corrections
~~~~~~~~~~~~~~~~~~~~~~~

Colorimeters generally need an initial factory correction with an actual spectrometer to be considered
accurate. Additionally, as the filters age and degrade over time, their spectral response change and
they may require measurement of new corrections regularly.

A poorly-corrected colorimeter will measure biased X, Y and Z values (due to metamerism_) for
certain types of colors, and in particular:

* The bias will be stronger for more **saturated colors**, resulting in perception mismatches.

* Measurements on **different display technologies** (different LED types and spectra) will be
  biased differently, making comparisons and accurate profiling very difficult or even
  impossible.

There are several types of corrections, with at least 2 being widely use in commercial colorimeters:

* **Correction matrixes**
* **Spectral measurements**

Colorimeter technologies
~~~~~~~~~~~~~~~~~~~~~~~~

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
.. _metamerism: https://en.wikipedia.org/wiki/Metamerism_(colorç)
