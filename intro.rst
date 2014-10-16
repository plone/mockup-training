Introduction
============

Mockup is the new frontend library for Javascript development, which is going
to be used plone.app.widgets and Plone 5.


The Goals of Mockup
-------------------

1. Standardize configuration of patterns implemented in js to use HTML data
   attributes, so they can be developed without running a backend server.

2. Use modern AMD approach to declaring dependencies on other js libs.

3. Full unit testing of js.


Technologies used with Mockup
-----------------------------

Mockup is much about JavaScript, and so it uses a JavaScript toolset, which is
quite common among JavaScript developers. This toolset includes:

- `Bower <http://bower.io/>`_ (`Github <https://github.com/bower/bower>`_, `Wikipedia <http://en.wikipedia.org/wiki/Bower_(software)>`_) for package management.

- `Grunt <http://gruntjs.com/>`_ (`Github <https://github.com/gruntjs/grunt>`_) for running repetitive tasks like combining files, minifying JavaScript, creating bundles and more.

- `RequireJS <http://requirejs.org/>`_ (`Github <https://github.com/jrburke/requirejs>`_)
  for defining dependencies between JavaScript modules. It uses the
  `Asynchronous Module Definition <https://github.com/amdjs/amdjs-api/blob/master/AMD.md>`_
  approach, opposed to the what the `CommonJS Module Definition <https://github.com/cmdjs/specification/blob/master/draft/module.md>`_ is defining.
  There is a document, `explaining the reason behind AMD <http://requirejs.org/docs/whyamd.html>`_, which is worth a read.
  With the upcoming ECMA Script 6 standard, we will get JavaScript module
  definitions and dependency declarations `built into the Language <http://www.2ality.com/2014/09/es6-modules-final.html>`_.

- `Yeoman <http://yeoman.io/>`_ (`Github <https://github.com/yeoman>`_, `Wikipedia <http://en.wikipedia.org/wiki/Yeoman_(computing)>`_) for generating pattern scaffolds.

- `LESS <http://lesscss.org/>`_ (`Github <https://github.com/less>`_, `Wikipedia <http://en.wikipedia.org/wiki/Less_(stylesheet_language)>`_) as CSS preprocessor.

- `NodeJS <http://nodejs.org/>`_ (`Github <https://github.com/joyent/node>`_, `Wikipedia <http://en.wikipedia.org/wiki/Node.js>`_) as a requirement for Grunt.


`<>`_ (`Github <>`_, `Wikipedia <>`_)

As always, some of these technologies can be discussed controversially. There
are other options for package management, build infrastructure, declaring
dependencies, preprocessing CSS - nearly for each aspect of Mockup. JavaScript
has an insanely fast moving ecosystem. Furtunatly, many Frameworks are quite
excellent. Finally we had to decide for some of these Frameworks. Mockup is
using well proven and widely used Frameworks. For sure, we will have to adapt
Mockup to fit to changed conditions in the future, but we're well of with the
tehcnologies choosen.
