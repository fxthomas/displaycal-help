Choosing a measurement device
=============================

Since DisplayCAL is all about measuring the display characteristics, we will need a measurement device.

What are we looking for?
------------------------

In order to measure our display, we need a way to transform the color we see with our eyes into
numbers that can then be tuned to achieve the desired characteristics.

When a pixel is given an RGB value as input, the light it emits can be fully characterised by its
spectrum_, a continuous measurement of infinitely many energy values emitted (radiance_) for *all*
wavelengths. Changing the spectrum of the light changes several related aspects of the perceived
color at the same time: brightness, hue, saturation, etc.

.. note::

Obviously, storing infinitely many values to fully represent a spectrum is infeasible, and in fact
it's even difficult and wasteful to manipulate a finite amount of spectrum measurements that is good
enough to represent colors accurately.

Because our eyes have 3 main types of color sensors, it turns out that we can in fact reduce a
spectrum to only **3 values: X, Y and Z**, computed from the characteristics of our eyes, which
together form the CIE-XYZ_ space. The instruments in this page are all more or less accurate ways of
getting these 3 values.

.. note::

   CIE-XYZ_ plays a similar central role as e.g. UTF-8 for text encoding, GMT for timezones or WGS84
   for GPS coordinates. Many (if not all) applications related to color go through CIE-XYZ as a good
   intermediate representation of colors as perceived by humans.

   For the purpose of this document, CIE-XYZ_ values completely represent a color unless explicitly
   indicated.

   Properties of perceived light like brightness, hue, saturation have precise definitions (usually
   derived from the spectrum) in several contexts.

In general all instruments consist of:

* Something to collect light in front of the device (usually a lens)
* Something to measure light (a sensor similar to a single pixel in a camera e.g. photodiodes,...)
* Something that converts the raw sensor values into CIE-XYZ_ measurements

Spectrometers
-------------

A spectrometer can record spectral samples simultaneously across a range of wavelengths (usually the
visible range), sometimes measuring hundred of values.

The output of a spectrometer is a spectrum, or a list of wavelengths and their corresponding light
intensity. The X, Y and Z values we want are then computed directly from the measured spectrum.

The biggest advantage of spectrometers when measuring colors is their **accuracy** since they
measure a spectrum directly and not derived values, and (unlike other solutions like colorimeters)
they're generally not biased by what color they're set to measure.

The largest disadvantage is their **cost**. Another disadvantage is their **measurement speed**
(especially for dark colors). They're also somewhat more **complex**: the spectrum they measure
needs to be accurate enough for all wavelengths and not just 3 values.

DisplayCAL will generally use a spectrometer just like a colorimeter, except when generating a
colorimeter correction.

Colorimeters
------------

A colorimeter consists of 3 **color filters** and their associated sensors, that specifically target
the parts of the light we need to measure X, Y and Z separately.

.. note::

   For the curious, `X-Rite i1 Display PRO teardown <https://www.youtube.com/watch\?v\=QAwKOGSow-s>`_ shows the
   various filters inside a very common colorimeter that is well-supported by DisplayCAL. `This page
   <https://displaycalibrations.com/x-rite_i1_measurement_solutions_info.html>`_ contain more technical information
   about the technical specifications of this specific model.

Colorimeters generally have an advantage over other methods in terms of **price**, but also in terms
of **speed**: you can use much bigger, and therefore less noisy sensors when you only have 3 of
them.

The biggest disadvantage of colorimeters is their **accuracy** if not enough care is given, since
their filters never perfectly match CIE-XYZ. Most models ship with a factory correction to
compensate for that, but this means they also require a spectrometer from time to time to refresh
that correction.

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

There are several types of corrections, with at least 2 being widely use in commercial colorimeters
and supported by DisplayCAL:

* **Correction matrixes**: We compute a simple linear relationship exists between the 3 channels of
  the colorimeter and the 3 X, Y, Z channels in CIE-XYZ. Such a correction needs to be measured for
  every combination of colorimeter and display panel.

* **Spectral measurements**: Some higher-end colorimeters provide measurements of spectral
  sensitivity of their filters. This correction lets us reuse existing display panel measurements
  (such as from technical specifications or an online database) with several colorimeters.

Colorimeter technologies
~~~~~~~~~~~~~~~~~~~~~~~~

Examples of supported colorimeters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _spectrum: https://en.wikipedia.org/wiki/Electromagnetic_spectrum
.. _CIE-XYZ: https://en.wikipedia.org/wiki/CIE_1931_color_space
.. _metamerism: https://en.wikipedia.org/wiki/Metamerism_(colorç)
.. _luminance: https://en.wikipedia.org/wiki/Luminance
.. _radiance: https://en.wikipedia.org/wiki/Radiance
