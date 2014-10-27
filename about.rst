About Mastering Mockup
======================

.. note::
    This training materials are in a work in progress state. You can contribute
    and help getting it better!

This training was created by `Johannes Raggam <https://github.com/thet>`_ and
`Franco Pellegrini <http://github.com/frapell>`_  to teach about `Mockup
<http://plone.github.io/mockup/>`_, the new Frontend library for `Plone 5
<https://github.com/plone/buildout.coredev/tree/5.0>`_ at the `Plone Conference
2014 <http://2014.ploneconf.org>`_ in Bristol.

The basic idea about this training (and even the boilerplate for this
materials) was stolen from Philip Bauer's and Patrick Gerken's `Mastering Plone
<https://github.com/plone/training>`_ materials. That is:

    The aim is that anyone with the appropriate knowledge can give a training
    based on it and contribute to it.  It is published as Open Source on
    Github and readthedocs.

This training materials are available on `Github
<https://github.com/plone/mockup-training>`_ and readthedocs (To be done).


Trainers
--------

The following trainers have given trainings based on Mastering Mockup:

Johannes Raggam
    Johannes Raggam from Graz/Austria works most of the time with a technology
    stack based around Python, Plone, Pyramid and Javascript. As an active Open
    Source / Free Software developer he believes in the power of collaborative
    work. He is BlueDynamics Alliance Partner and Plone Core Contributor since
    2009 and member of the Plone Framework Team since 2012.

Franco Pellegrini
    Franco Pellegrini is a software developer from Cordoba, Argentina. He
    started developing Plone in 2005 in a small software company, and as an
    independent contractor since 2011. He believes in free software philosophy,
    and so, he has been a Plone core developer since 2010 and Framework Team
    member since 2012.


Using the documentation for a training
---------------------------------------

Feel free to organize a training yourself. Please be so kind to contribute any bugfixes or enhancements you made to the documentation for your training.

The training is rendered using sphinx and builds in two flavors:

default
    The verbose version used for the online-documentation and for the trainer. Build it in sphinx with ``make html`` or use the online-version.

presentation
    A abbreviated version used for the projector during a training. It should uses more bullet-points than verbose text. Build it in sphinx with ``make presentation``.

.. note::

    By prefixing an indented block of text or code with ``.. only:: presentation`` you can control that this block is used for the presentation-version only.

    To hide a block from the presentation-version use ``.. only:: not presentation``

    Content without a prefix will be included in both versions.


The readthedocs-theme
+++++++++++++++++++++

We slightly tweaked readthedocs-theme in ``_static/custom.css`` so that it works better with projectors:

- We start hiding the navbar much earlier so that it does not interfere with the text.
- We enlarge the default width of the content-area.

Excercises
++++++++++

Some additional javascript shows hidden solutions for exercises by clicking.

Just prepend the solution with this markup::

    ..  admonition:: Solution
        :class: toggle

Here is a full example::

    Exercise 1
    ^^^^^^^^^^

    Your mission, should you choose to accept it...

    ..  admonition:: Solution
        :class: toggle

        To save the world with only seconds to spare do the following:

        .. code-block:: python

            from plone import api

It will be rendered like this:

Exercise 1
^^^^^^^^^^

Your mission, should you choose to accept it...

..  admonition:: Solution
    :class: toggle

    To save the world with only seconds to spare do the following:

    .. code-block:: python

        from plone import api


Building the documentation locally
++++++++++++++++++++++++++++++++++

To build the documentation follow these steps:

.. code-block:: bash

    $ git clone https://github.com/plone/mockup-training.git
    $ cd mockup-training
    $ virtualenv-2.7 .
    $ source bin/activate
    $ pip install -r requirements.txt
    $ make html

You can now open the output from ``_build/html/index.html``. To build the presentation-version use ``make presentation`` instead of ``make html``. You can open the presentation at ``presentation/index.html``.


Contributing
------------

Everyone is **very welcome** to contribute. Minor bugfixes can be pushed direcly in the `repository <https://github.com/plone/training>`_, bigger changes should made as `pull-requests <https://github.com/plone/training/pull/>`_ and discussed previously in tickets.


License
-------

The Mastering Mockup Training is licensed under a `Creative Commons Attribution 4.0 International License <http://creativecommons.org/licenses/by/4.0/>`_.

Make sure you have filled out a `Contributor Agreement <http://plone.org/foundation/contributors-agreement>`_.

If you haven't filled in a Contributor Agreement, you can still contribute. Contact the Documentation team, for instance via the `mailinglist <http://sourceforge.net/p/plone/mailman/plone-docs/>`_ or directly send a mail to plone-docs@lists.sourceforge.net
Basically, all we need is your written confirmation that you are agreeing your contribution can be under Creative Commons. You can also add in a comment with your pull request "I, <full name>, agree to have this published under Creative Commons 4.0 International BY".

