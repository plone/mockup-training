Installation and Bootstrapping
==============================


Prerequisites
-------------

To build and hack on Mockup you will need recent versions of git, node, npm, PhantomJS and make.

Right now development of this project is being done primarily on Linux and OS X,
so setting up the tooling on MS Windows might be an adventure for you to explore --
though, all of the tools used have equivalent versions for that platform,
so with a little effort, it should work!

* Node 0.10 or up (Installation via `package manager
  <https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager>`_
  or by `building <https://github.com/joyent/node/wiki/Installation>`_).


* PhantomJS (Use your package manager or `download and install
  <http://phantomjs.org/download.html>`_).


* Make


Installing Mockup
-----------------

Mockup is installed by cloning a git repository and run ``make bootstrap`` then::

    $ git clone https://github.com/plone/mockup.git
    $ cd mockup
    $ make bootstrap


Now you have the complete source code for all Patterns from Mockup.
From here on you generate bundles of common functionality and minify them.

You're ready to start working on testable, modular and beautiful JavaScript!


Building the documentation and examples
---------------------------------------

To see it in action, you must compile everything once, with::

    $ make docs

Then, start the python test server like so::

    python -m SimpleHTTPServer

After that, access the served site in a webbrowser via the url http://localhost:8000


Running tests
-------------

Run tests with PhantomJS and continue to listen for changes::

    $ make test

Run tests with Chrome::

    $ make test-dev

Or run the tests for an individual plugin::

    $ make test-once pattern=select2


More Makefile commands
----------------------

The ``Makefile`` provides this list of commands::

    all                 Tests everything once, creates all default bundles and builds the documentation.
    bootstrap           Bootstrap Mockup. Cleans the environment (deletes node_modules and bower_components) and installs npm and bower dependencies.
    bootstrap-common    Common tasks for other bootstrap tasks. Not intended to be run manually.
    bootstrap-nix       Bootstraps Mockup for NixOS environments. It installs all dependencies via the nix package manager. For nix users.
    bundle-filemanager  XXX
    bundle-plone        Builds the Plone bundle.
    bundle-resourceregistry Builds the bundle for the new resource registry.
    bundle-structure    XXX Builds the structure (content browser) bundle.
    bundle-widgets      Builds the widgets bundle.
    bundles             Builds all the default bundles (bundle-widgets, bundle-structure, bundle-plone).
    clean               Clean the environment by removing the build, node_modules and bower_components directory.
    clean-deep          Clean the environment like with ``clean`` and additionally clean bower's and node's cache.
    docs                Builds the Mockup documentation.
    jshint              Run the code quality suite (jshint and jscs).
    publish-docs        Publish the github pages documentation.
    test                Run Mockup's tests and keep watching for file changes. Accepts the option [--pattern=PATTERNNAME] to define a specific pattern.
    test-ci             Run the tests on the Continious Integration server environment.
    test-dev            Run Mockup's tests in the Chromium browser and keep watching for file changes. Accepts the [--pattern=PATTERNNAME] option to define a specific pattern.
    test-once           Run Mockup's tests only once. Accepts the [--pattern=PATTERNNAME] option to define a specific pattern.
    watch               Watches for file changes and rebuilds Mockup.

All tests also accept the experimental ``--debug`` and ``--verbose`` options to
help with debugging by changing the verbosity of the log messages.


Including a local mockup-core checkout for developing
-----------------------------------------------------

If you want to also hack on mockup-core together with mockup, you should
include it from a local checkout. Bower allows to point to a ``.git`` directory
for referencing local repositories. Just replace the ``mockup-core`` dependency
in ``bower.json`` with::

    "mockup-core": "file:///PATH/TO/mockup-core/.git/#BRANCHNAME"

Please note, you have to commit any changes on mockup-core and then run ``make
bootstrap`` in mockup again.
