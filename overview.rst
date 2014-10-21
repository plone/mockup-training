Overview of Mockup
==================

Mockup Nomenclature
-------------------

Patterns
    Patterns are units of JavaScript, defined by a RequireJS/AMD style module.
    Patterns may require other patterns to operate, and may also require third
    party libraries.  Think of a pattern as a module -- encapsulated and
    separate, and providing a widget or tool to be used by other patterns or in
    html.

Bundles
    Bundles are defined in a similar way to *Patterns* -- they are encapsulated
    bits of JavaScript that define requirements for a bundle and have some
    extra code in them that's useful for integrating the required patterns into
    Plone products.


Mockup Project Structure
------------------------

``build/``: Contains the builded bundles. This are combined, optimized, and
minimized JavaScript code, as well as the compiled CSS (Less) and media files
from a bunlde's dependencies.

``docs/``: Mockup documentation files and examples built with ``make docs``.

``js/config.js``: RequireJS configuration. This is the file, where all
JavaScript dependencies are defined, so that RequireJS is able to find them via
a name.

``js/bundles``: The directory, where Mockup's bundles are defined.

  - ``js/patterns`` : Contains all individual, encapsulated patterns
      e.g. widgets.js

- ``less/`` : Contains all the [Less](http://lesscss.org/) code for all the patterns and bundles

- ``lib/`` : Contains external libraries not necessarily found in the bower repositories

- ``tests/`` : Contains all tests for patterns and bundles, including general setup and configuration code

- ``Gruntfile.js`` : Defines the directives for compiling Less,
   and for combining/optimizing/minimizing JavaScript to the defined bundles

- ``index.html`` : The main source of documentation for the mockup project

- ``Makefile`` : Scripts to build bundles, bootstrap the environment etc.
