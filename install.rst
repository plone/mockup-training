Installation and Bootstrapping
==============================


Normal Installation
-------------------

The normal way to install `Mockup` is to directly install it to your system,
using the system's `Node` version and other tools. If this is not possible,
because you are using Windows or don't want to pollute your System with
libraries not necessarily needed, use the :ref:`vagrant_installation` method.

Prerequisites
~~~~~~~~~~~~~

To build and hack on Mockup you will need recent versions of ``git``, ``node``,
``npm``, ``PhantomJS`` and ``make``.

- Installing Node: You need to have Node 0.10 or newer. Normally, NPM is
  installed together with node. For installation instructions see `Installation
  via package manager
  <https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager>`_
  or `Building Node <https://github.com/joyent/node/wiki/Installation>`_.

- Installing PhantomJS: Use your package manager or `download and
  install <http://phantomjs.org/download.html>`_).

.. note::
    There is a useful tool, which helps you to install different versions of
    Node, if you need it. The `Node Version Manager
    <https://github.com/creationix/nvm>`_, ``nvm``. Try it, if you run into
    problems with your system's Node version.

Right now development of this project is being done primarily on Linux and OS X,
so setting up the tooling on MS Windows might be an adventure for you to explore --
though, all of the tools used have equivalent versions for that platform,
so with a little effort, it should work!


Installing Mockup
~~~~~~~~~~~~~~~~~

Installing `Mockup` is as easy as cloning and then running `make bootstrap`::

    $ git clone https://github.com/plone/mockup.git
    $ cd mockup
    $ make bootstrap

This bootstraps the whole application. It cleans up the directory and installs
node and bower dependencies.


.. _vagrant_installation:

Installing Mockup with Vagrant
------------------------------

Vagrant can be a great choice, if you don't want to install Mockup and it's
dependencies directly to your machine, possibly polluting your environment
(but normally, Mockup doesn't install anything globally). Vagrant is also a
great choice, if you want to provide the same environment for every developer.
Therefore we choosed it as the recommended installation method for our Mockup
training.

With this method, Mockup is installed by cloning a git repository on a VM host
to obtain a Vagrantfile.  A guest VM (Ubuntu) is started with the Vagrantfile
and provisioned with Mockup prerequisites.  Then a bootstrap script is run on
the guest VM. Follow these steps:

1. Install VirtualBox: https://www.virtualbox.org. Use your system's package
   manager, if you have one. 

2. Install Vagrant: http://www.vagrantup.com. If you have such a thing
   like a system package manager, I recommend to use it only, if it includes a
   recent version of Vagrant.

3. If you are using Windows, install the Putty ssh kit:
   http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html. Install all
   the binaries, or at least putty.exe and plink.exe.


Now we can install Mockup itself:

.. code-block:: bash

    $ # The following run on the host OS:
    $ git clone https://github.com/plone/mockup.git
    $ cd mockup
    $ vagrant up

Now, go for lunch or a long coffee break. "vagrant up" is going to download a
virtual box kit (unless you already happen to have a match    Windows, it will
also generate an ssh key pair that's usable with Putty.

.. note::
    While running "vagrant up", feel free to ignore messages like "stdin: is
    not a tty" and "warning: Could not retrieve fact fqdn". They have no
    significance in this context.

Look to see if the install ran well. The virtual machine should be running at
this point:

.. code-block:: bash

    $ vagrant reload
    $ vagrant ssh


Now you are logged into your virtual machine:

.. code-block:: bash

    $ # The following run on the guest VM:
    $ cd /vagrant
    $ git pull
    $ make bootstrap

Now you have the complete source code for all Patterns from Mockup.
From here on you generate bundles of common functionality and minify them.

You're ready to start working on testable, modular and beautiful JavaScript!

.. note::
    Parts of this instructions are based on the `plonedev.vagrant README.rst
    <https://github.com/plone/plonedev.vagrant/blob/master/README.rst>`_. Have
    a look for it, if you need more information and troubleshooting
    instructions.


Working with Mockup
-------------------

Building the documentation and examples
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To see it in action, you must compile everything once, with:

.. code-block:: bash

    $ make docs

Then, start the python test server like so:

.. code-block:: bash

    $ python -m SimpleHTTPServer

After that, access the served site in a webbrowser via the url http://localhost:8000


Running tests
~~~~~~~~~~~~~

Run tests with PhantomJS and continue to listen for changes:

.. code-block:: bash

    $ make test

Run tests with Chrome:

.. code-block:: bash

    $ make test-dev

Or run the tests for an individual plugin:

.. code-block:: bash

    $ make test-once pattern=select2


.. _makefile-commands:

More Makefile commands
~~~~~~~~~~~~~~~~~~~~~~

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
~~~~~~~~~~~~~~~~~~~~

After changes to bower.json, you don't have to run ``make bootstrap``, which
wipes all dependencies and starts installing them all over again. You can use
bower directly:

.. code-block:: bash

    $ bower search PACKAGENAME  # search online for a package in the bower registry
    $ bower list  # list all dependencies and possible updates
    $ bower install  # install all dependencies listed in bower.json
    $ bower update  # update all dependencies to the versions specified in bower.json

For more information, see the `bower API documentation <http://bower.io/docs/api/>`_.


Including a local mockup-core checkout for developing
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you want to also hack on `mockup-core
<https://github.com/plone/mockup-core>`_ together with mockup, clone
mockup-core into a directory on your machine and just symlink it into
bower_components::

    $ cd ..
    $ git clone https://github.com/plone/mockup-core
    $ cd mockup/bower_components
    $ rm -R mockup-core
    $ ln -s ../../mockup-core .

.. note::
    You can also point bower.json to a local git checkout. You have to point
    bower directly to the `.git` subdirectory and declare the branchname in
    order to be able to use a local checkout. For that, replace the
    `mockup-core` line in `bower.json` with something like the following::

        "mockup-core": "file:///PATH/TO/mockup-core/.git/#master"

    Please note, you have to commit any changes on mockup-core and then run
    ``bower install``, ``bower update`` or ``make bootstrap`` in mockup again.
