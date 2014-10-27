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


.. note::
    There is a useful tool, which helps you to install different versions of
    Node, if you need it. The `Node Version Manager
    <https://github.com/creationix/nvm>`_, ``nvm``. Try it, if you run into
    problems with your system's Node version.


Installing Mockup
-----------------

Mockup is installed for this training by cloning a git repository on a VM host to obtain a Vagrantfile.
A guest VM is started with the Vagrantfile, started, and provisioned with Mockup prerequisites.
Then a bootstrap script is run on the guest VM::

    $ # The following run on the host OS:
    $ git clone https://github.com/plone/mockup.git
    $ cd mockup
    $ vagrant up
    $ vagrant reload
    $ vagrant ssh
    $ # The following run on the guest VM:
    $ cd /vagrant
    $ git pull
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


.. _makefile-commands:

More Makefile commands
----------------------

The ``Makefile`` provides this list of commands::

    all                 Tests everything once, creates all default bundles and builds the documentation.
    bootstrap           Bootstrap Mockup. Cleans the environment (deletes node_modules and bower_components) and installs npm and bower dependencies.
    bootstrap-common    Common tasks for other bootstrap tasks. Not intended to be run manually.
    bootstrap-nix       Bootstraps Mockup for NixOS environments. It installs all dependencies via the nix package manager. For nix users.
    bundle-filemanager  Builds the resourceeditor filemanager bundle.
    bundle-plone        Builds the Plone bundle.
    bundle-resourceregistry Builds the bundle for the new resource registry.
    bundle-structure    Builds the structure bundle (wildcard.foldercontents content browser).
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


Using Bower directly
--------------------

After changes to bower.json, you don't have to run ``make bootstrap``, which
wipes all dependencies and starts installing them all over again. You can use
bower directly::

    $ bower search PACKAGENAME  # search online for a package in the bower registry
    $ bower list  # list all dependencies and possible updates
    $ bower install  # install all dependencies listed in bower.json
    $ bower update  # update all dependencies to the versions specified in bower.json

For more information, see the `bower API documentation <http://bower.io/docs/api/>`_.


Including a local mockup-core checkout for developing
-----------------------------------------------------

If you want to also hack on mockup-core together with mockup, you should
include it from a local checkout. Bower allows to point to a ``.git`` directory
for referencing local repositories. Just replace the ``mockup-core`` dependency
in ``bower.json`` with::

    "mockup-core": "file:///PATH/TO/mockup-core/.git/#BRANCHNAME"

Please note, you have to commit any changes on mockup-core and then run ``bower
install``, ``bower update`` or ``make bootstrap`` in mockup again.
