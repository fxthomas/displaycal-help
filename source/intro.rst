Introduction to DisplayCAL
==========================

DisplayCAL_ is an open-source software that provides a user interface for measuring and
characterizing various types of computer displays, including generation and management of ICC
profiles, as well as generation of 3D LUTs compatible with video editing programs.

DisplayCAL is based on ArgyllCMS_, a collection of command-line tools with the more general purpose
of characterizing all kinds of input and output devices capable of recording or producing colors,
whether analog or digital (displays, cameras, printers, scanners, etc.), but you will in most cases
not need to interact with ArgyllCMS directly.

.. figure:: _static/images/main-window.png
   :width: 600
   :align: center


Do I need DisplayCAL?
---------------------

DisplayCAL is useful for situations where an image needs to be perceived similarly on multiple
surfaces, including rendering of color but also other attributes such as perceived contrast and
brightness. Common scenarios are:

* Displaying images side-by-side on multiple computer displays, for example when comparing similar
  photographs.
* Comparing images between a computer display and printed reproductions using a calibrated or
  profiled printer (generating printer profiles being out of scope for DisplayCAL).

In a lot of cases you do *not* need DisplayCAL for displaying images on a single display. Most
displays are tested for sRGB_ in mind (the standard for images displayed over the internet) ; the
display may be more or less accurate or embed additional rendering tweaks (saturation, contrast,
white point), but outside of extreme cases the differences are almost unnoticeable in day-to-day
usage once your eye is adapted to the display. A few exceptions exist, such as:

* Ensuring rendering of an image is neutral and does not influence perception while editing
  photographs that will be shared over the internet (for example when editing using consumer
  displays or TVs with very opinionated factory renderings showing high saturation/contrast compared
  to sRGB_).
* Ensuring rendering of a video follows a specific standard in order to perform
  color grading (e.g. Rec.1886_ with Rec.709_ primaries).

A good introduction to color management is available in the `Krita documentation
<https://docs.krita.org/en/general_concepts/colors/color_managed_workflow.html>`_. Before deciding
whether you need DisplayCAL, you should at least be familiar with the basic concepts explained here.


How does DisplayCAL work?
-------------------------

To display an image or video accurately on a computer display, you need to know both how the display
behaves (the **display** or **target profile**) and how the image is supposed to be displayed (the
**image** or **source profile**) in order to build a conversion (**link profile**) between the two:

* DisplayCAL and other profiling software are responsible for measuring the actual behavior of a
  computer display into a display profile.

* Images can optionally be tagged with their source profile, in most cases (though not always)
  representing an ideal display on which they are supposed to be displayed ; images with no tags
  usually assume sRGB_.

.. figure:: _static/images/displaycal-colormanaged-workflow.svg
   :width: 600
   :align: center

.. note::
   In this context, we are talking about ICC profiles, but for completeness DisplayCAL also supports
   generation of "3DLUT" (3D Look-Up Tables) files that can serve a similar role. These files are
   generally in use for video production software.

ICC profiles can be registered with the operating system (on both Windows and Linux), but the
responsibility of actually retrieving and using them properly is entirely delegated to the program
displaying the image.

* Specialized graphics programs (Krita, Inkscape, GIMP, Darktable, Digikam, etc) are usually
  **color-managed**. They can automatically pick up a registered display profile and provide various
  options as to how an image should be rendered using both the image's internal profile and the
  display profile using a **Color Management Module** (CMM).

* Some general-purpose programs (e.g. Firefox, Gwenview, Chrome, the Windows Explorer and Photo
  viewer,...) are **color-aware**, sometimes only partially. They are generally at least aware of
  the image's internal profile, sometimes only for a subset of supported formats, but may ignore the
  registered display profile (defaulting to a common ideal display profile such as sRGB_) or provide
  a limited set of configuration options from their CMM.

* Most programs are by default **color-unaware**, and will ignore both display and image profiles.




.. _DisplayCAL: https://displaycal.net/
.. _ArgyllCMS: http://argyllcms.com/
.. _sRGB: https://en.wikipedia.org/wiki/SRGB
.. _Rec.1886: https://en.wikipedia.org/wiki/ITU-R_BT.1886
.. _Rec.709: https://en.wikipedia.org/wiki/Rec._709
