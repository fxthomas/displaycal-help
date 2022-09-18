Choosing a display system
=========================

While DisplayCAL will work on almost any display, knowing a little more about the intended characteristics of the
display can help a lot, especially when considering a purchase.

The ability of profiles to reproduce colors is directly linked to the manufacturer specification (and to how well the
display matches them in reality), but profiles may be more or less accurate depending on the presence or absence of some
features on the display.

Main characteristics
--------------------

All computer displays, regardless of the underlying technology, provide an array of pixels, each pixel being split into
3 very small RGB (Red, Green and Blue) subpixels whose intensity is independently controllable from 0 to 100%.

One may distinguish:

* The **input signal**, which corresponds to the RGB intensity control, in percentage, for a given pixel.
* The **output light**, which corresponds to the light physically emitted by the display in response to an input
  signal.

A large number of `display technologies`_ exist, whose behavior may vary in terms of the exact spectrum (color) of each
RGB subpixel as well as non-ideal behaviors in different areas.

Primaries and gamut coverage
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Each of these RGB subpixels emits a given spectrum, but because they are too small to be perceieved individually by our
human eye we instead perceive only their sum. This is called the `additive model`_ of color.

The spectrum of each RGB component at 100% input signal is usually called **primaries**, generally assumed to be
constant all over the surface of the screen.

The word **gamut** refers to all the colors formed by adding any combination of intensities of the 3 primaries.

Many manufacturer specifications contain the display's **gamut coverage**, which refers to how many colors their display
can reproduce for a set of reference primaries.

For example, saying "100% sRGB" means that the display can reproduce all possible colors that can be described by the
sRGB primaries. Saying "50% Rec.2020" means that the display can only reproduce half the colors in Rec.2020 -- usually
with the assumption that the more saturated colors cannot be reproduced.

.. tip::
   When doing color-related work, you should aim for a display that can reproduce at least 100% sRGB gamut, since this
   is the *de facto* standard for web content and usually covers most consumer-grade printers.

.. note:: In the CIE-xy_ space, the 3 primaries form a triangle, and the the gamut is the area inside the triangle,
   where each point represents a more or less saturated hue, independant on the intensity of the color. The gamut
   coverage is the proportion of the triangle formed by the reference primaries that intersects with the triangle formed
   by the display primaries.

White point
~~~~~~~~~~~

The `white point`_ of a display corresponds to the spectrum of the light emitted when trying to display a neutral color
(perceived as gray or white), with all RGB components of an input signal equal to the same value.

Luminance curves
~~~~~~~~~~~~~~~~

The intensity control of a given R, G or B channel never fully corresponds to the intensity of the light emitted by a
corresponding subpixel ; we say it's nonlinear_: when doubling the intensity control, the light intensity emitted by the
pixel doesn't double but instead follows an arbitrary curve.

Nonlinearities and non-ideal behaviors
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In some cases, reducing the peak luminance used during calibration will mitigate part of these effects, allowing the
generated profile to be more accurate while effectively reducing the brightness of the display.

All display systems 

Display pipeline and controls
-----------------------------

Application-level controls
~~~~~~~~~~~~~~~~~~~~~~~~~~

The intensity control may be located, logically, at different levels of the display pipeline from RGB values sent by
the application to the actual current flowing through thr RGB subpixels, and may be modified by any layer inbetween:
application color management, OS color management settings, driver settings, display settings, etc.

System-level controls
~~~~~~~~~~~~~~~~~~~~~

Hardware controls
~~~~~~~~~~~~~~~~~

Display uniformity
------------------

Profiling generally assumes a display is uniform.

Vignetting
~~~~~~~~~~

Anisotropy and directionality
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Glare
~~~~~

Display dynamics
----------------

Temperature drift
~~~~~~~~~~~~~~~~~

Aging
~~~~~

Automatic Brightness Limiter (ABL)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Other considerations
--------------------

Content-dependent brightness limiters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some laptop displays (for example, using the "Dell Intelligent Display" technology or Intel's power-saving
optimizations) automatically adapt display characteristics (brightness and contrast) to the content of the screen ; for
example, a full-screen dark application window will be displayed with a different luminance curve than a white
application window.

This needs to be turned off to use DisplayCAL properly, as it will interfere with profiling.

Ambient light sensors (ALS)
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some laptop displays feature an ambient light sensor, which automatically adapts the display characteristics to the
ambient light.

This needs to be turned off to use DisplayCAL properly, as it will interfere with profiling.

Night light
~~~~~~~~~~~

Some software allows the display white point to be adapted to the time of the day, making colors appearing warmer (less
blue) when at night to avoid eye strain.

In general this needs to be turned off to use DisplayCAL properly.

An alternative option, if you absolutely need to calibrate your display to warmer colors while conserving accuracy for
color-managed applications, is to lower the white point color temperature setting in DisplayCAL calibration panel.

RGBW displays
~~~~~~~~~~~~~

Some displays (in particular HDR displays, but also some projectors) mix low-resolution white pixels amidst regular RGB
pixels in order to make some parts of the image brighter, at the expense of altering colors and contrast.

These displays are difficult to profile properly with DisplayCAL, not only because the white channel is almost never
exposed as an input signal to the user, but also because most of that logic is activated automatically inside the
display hardware and will be heavily dependent on the content being displayed.

Some of these displays provide a way to disable this feature, which will allow profiling with DisplayCAL but will on the
other hand reduce the maximum luminance supported by the display.


.. _additive model: https://en.wikipedia.org/wiki/Additive_color
.. _nonlinear: https://en.wikipedia.org/wiki/Nonlinear_system
.. _display technologies: https://en.wikipedia.org/wiki/Comparison_of_display_technology
.. _white point: https://en.wikipedia.org/wiki/White_point
.. _CIE-xy: https://en.wikipedia.org/wiki/CIE_1931_color_space#CIE_xy_chromaticity_diagram_and_the_CIE_xyY_color_space
