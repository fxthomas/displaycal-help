I'm writing this documentation in the hopes that it may help newcomers understand how to use DisplayCAL more
effectively.

It is not at the moment a replacement for DisplayCAL's [reference documentation](https://displaycal.net), and will not
contain an exhaustive explanation of all settings and features. That may become a goal in the future, but is not a
priority for me at the moment.

How to build
============

Install requirements:

    pip install --user -r requirements.txt

Build the HTML docs:

    make html

How to develop
==============

Use the following command (requires the `inotifywait` command) to rebuild the documentation each time a file is changed:

    make watch

Use the following command (requires Python) to start a simple web server and open the start page of the documentation:

    make serve

License
=======

I haven't chosen a license yet ; for now this is still under my copyright, but the eventual goal is to use a libre license so that it can be freely reused.

Some images are adapted from the Krita documentation.
