Create your own mockup project
==============================

As seen earlier in this training, one alternative to work with Mockup, is to pull the complete source from github, do your changes, removals and modifications and finally compile. This process, has obvious disadvantages, and for this, we have created a `generator <https://github.com/collective/generator-plonemockup>`_ that allows you to generate the bare minimum you need to start your project.


Dependencies
------------


System wide installation
++++++++++++++++++++++++

If you feel comfortable installing packages in your system, all you need for using the generator is `npm <http://npm.com>`_ and `yo <https://github.com/yeoman/yo>`_.
If you're on Ubuntu :

.. code-block:: bash

    $ sudo apt-get install npm nodejs-legacy
    $ npm install -g yo
    $ npm install -g generator-plonemockup


Using Vagrant
+++++++++++++

This is a fantastic alternative, if you don't want to pollute your system installing dozens of packages. It will create a virtual environment using Ubuntu 14.04, install all the needed dependencies, such as npm, less, grunt, and so on... so you don't have to bother about it.

Just pull the development version of the generator:

.. code-block:: bash

    $ git clone git@github.com:collective/generator-plonemockup.git

The relevant files are "Vagrantfile" and "provision.sh". Understanding and using Vagrant is out of this document scope. For now, all you need to care about is running any of the following commands inside the directory you have just cloned, that holds the Vagrantfile:

- ``vagrant up``

    This command start the virtual environment. When running it for the first time it will install and configure all needed packages.
    NOTE: Some of the output will be in red, this is normal.

- ``vagrant reload``

    This command will make the virtual environment to restart. You need to do this the first time

- ``vagrant ssh``

    Once the virtual environment is up and running, this command will ssh into the machine. This is like ssh'ing into any computer, all you need to do to exit is "Ctrl + D"

- ``vagrant halt``

    This command will turn off the virtual machine, issuing an ACPI shutdown, so it's safe to use it at any time.

- ``vagrant destroy``

    This command will destroy the virtual environment. Be aware that this will remove the entire virtual machine, be aware when using it.


For additional reading, go to `Vagrant homepage <https://www.vagrantup.com/>`_.


Creating your project
---------------------

We will now create our first project

Without using Vagrant
+++++++++++++++++++++

Just create a directory where your project will be. We'll call it "myproject". Inside this directory we can run our generator.


Using Vagrant
+++++++++++++

Make sure you run "vagrant ssh" to login to your virtual environment. When inside, you will be user "vagrant", which has full sudo privileges inside that machine.

the /vagrant directory will be our working directory, and is the same as the directory outside the virtual environment.

So, if you:

.. code-block:: bash

    vagrant@mockup-generator:~$ cd /vagrant/
    vagrant@mockup-generator:/vagrant$ ls

You should see the same content as you had from "the outside".

Go to /vagrant and create a directory for your project, we'll call it "myproject" and inside, we'll run our generator


Common steps
++++++++++++

From this point on, instructions are the same either you are running vagrant or not:

.. code-block:: bash

    $ cd myproject/
    $ yo plonemockup

The generator will ask a bunch of questions for generating the project and populating the packages.json among other things. They are detailed below

- ``Name for the project``

This is the name of the whole project, it is used for class and file names. You can put anything here, except for hyphens and spaces (This will get fixed eventually), so for now, we are going to name it "myproject"

- ``Version``

Self-explanatory. The version of your project. Make sure you use x.y.z format (ie. 3 numbers)

- ``Description``

An optional description, you can use any character in here.

- ``Homepage``

Optional, specify your project's URL

- ``Repository``

If you intend to publish this in a version control system, you can specify here the URL, it will default to https://github.com/collective/{packageName}, in our case https://github.com/collective/myparoject

- ``Author full name, email and webpage``

You can specify here your name, email address and a web site, to be included as metadata with your project

- ``License``

Choose the license fo your project. At the moment, GPLv2, GPLv3 and MIT are supported. You can modify the package later to provide your own if needed.

- ``Name for your pattern``

Here you can specify the name for a pattern you intend to develop. There is no way to not choose one at the moment, it will be in future versions. If you don't intend to develop a pattern, just put any name here, and you can remove it manually later.
We will be developing a new pattern, and we are going to call it "mypattern".
Just as the project name, avoid spaces and hyphens (This will be fixed too in future releases)


After answering all questions, your package is created and all dependencies are pulled in using bower and npm. Just wait until it finishes.
If you get an error at this moment, you can re-run 'npm install' and 'bower install' as needed.
When running the automated process for the first time, it may happen that the process just hangs. This might be because at one point, bower asked::

    [?] May bower anonymously report usage statistics to improve the tool over time?

and all the npm install output hides it... don't worry, just type 'yes' or 'no' and hit 'Enter'. Or if you intend to respond 'yes' anyway, just hit 'Enter' directly. You will see the above question printed again...


Working with your new package
-----------------------------

This will assume we have named our project 'myproject' and our pattern, 'mypattern'


Structure
+++++++++

The newly created package, has the full structure of files and directories ready for start developing::

    ├── bower.json
    ├── config.js
    ├── dev
    │   ├── dev.html
    │   └── dev.js
    ├── Gruntfile.js
    ├── js
    │   ├── bundles
    │   │   └── myproject.js
    │   └── patterns
    │       └── mypattern.js
    ├── less
    │   └── myproject.less
    ├── package.json
    ├── README.md
    └── tests
        ├── config.js
        └── pattern-mypattern-test.js


The 'dev' directory
+++++++++++++++++++

This is a helper folder. It provides a dev.html which already includes a basic html to start developing your pattern and includes the needed javascript files. The 'dev.js' file is the one that loads your bundle and pattern(s) automatically so you can start developing right away.


The 'js' directory
++++++++++++++++++

This is where your bundle and pattern(s) will be located.
You will be working mostly in js/patterns/mypattern.js if you are developing a new pattern, or in js/bundles/myproject.js if you are bringing additional patterns from mockup.


The 'less' directory
++++++++++++++++++++

This is where you will include the less files for your project


The 'tests' directory
+++++++++++++++++++++

This is where automated tests for your patterns will be written (And of course you will write them ;) )


config.js
+++++++++

In case you add new patterns, libraries, or need to tweak some paths, this is the file where you should do that.


Compiling and testing
---------------------

Once developing is done and you want to compile your work, just go to your project's root directory and run 'make':

.. code-block:: bash

    $ make

If you don't get any errors, you should endup with a new directory called build, where you will find your files ready to use
