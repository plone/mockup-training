Mockup development process
==========================

Code style
----------

Use jshint, and it will cover most code style issues. We included a ``.jshint``
file with Mockup's code style configuration. You can use this one in your
editor to automatically display syntax errors (E.g. by the plugin ``syntastic``
in vim, if you use it).

We use spaces instead of tabs and an indentation level of 2 spaces per tab.


Contributions
-------------

For each feature, create a branch and make pull-requests on Github. Try to
inclue all your changes in one commit only, so that our commit history stays
clean. Still, you can do many commits to not accidentliy loose changes and
still commit to the last commit by doing::

  git commit --amend -am"my commit message".

Don't forget to also include a changelog entry in the ``CHANGES.rst`` file.

