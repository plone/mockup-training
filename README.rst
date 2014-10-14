Mockup training materials
=========================

Initially created for the Mockup Training at Ploneconf 2014.
http://2014.ploneconf.org/training/mockup-training


Structure
=========

1) Theoretical part.

This will include an explanation on what we are doing with mockup and why.
Should we mention the different Javascript framework alternatives?  More here…

2) Go into detail with Mockup. Explain code structure and design ideas

3) Developing a pattern from scratch

4) Fixing/modifying/extending an existing “mockup pattern”

5) How to include an extra compiled js with new patterns to live along the
   default mockup one. What would happen if both files have the same pattern?


Training Description
====================

Here are some of my ideas about the training:

- The training should include theoretical and practical sessions.
- The theoretical part of the training can easily be used as the basis
  for a talk.
- In the practical part, we can work on missing patterns and let the
  participants create those. That way, we would get forward finishing
  mockup.

- Topic which should be covered:

  - Development environment (Using linters in your editor, Bower, Grunt)
  - How RequireJS works
  - How mockup works (project structure, patterns initialization)
  - Patterns scaffolding
  - Developing Patterns within mockup and as outside dependency
  - Developing with the new resource registry
  - Extra: Mockup vs Patternslib vs Web Components vs Angular JS
           directives


TODO
====

- Ask Matt about registered participants. [thet]
- Create repositories for training docs + talk slides (first privately (franco, thet), next week publish on github.com/plone) [thet]
- Fix plone.app.widgets on Windows [thet]
- List of missing patterns / issue trackers

- Next Meeting, thursday - 16th Oct, 15:00 CET / 10:00 Buenos Aires


- Want: make Mockup pluggable - adding a pattern without, injecting the
  dependency to mockup package itself. Otherwise, you'd always need an
  integration package.

Talk
====

For the talk, this is my talk from previous ploneconf and plone symposium:
http://www.slideshare.net/FrancoPellegrini/patterns-the-new-javascript-framweork

Quick n dirty notes
===================

@frapell's generator (will be used for training): https://github.com/collective/generator-plonemockup

generator, created @ zidanca sprint: https://github.com/collective/collective.pattern.generator


From previous mails
===================

- we need boilerplate code to get started. your generator and the one
from zidanca sprint are some, my plone.app.event pattern commit in
mockup is another.

- we need something like a tutorial documentation. peter gave me the
idea, that it's quite nice to have a written tutorial for participants
to follow, so that if someone is stuck and needs help from the trainers,
others can still work on.

- we need a list of missing mockup patterns to work on.

- about the presentation framework: what's your opinion on using
reveal.js? it's very nicely styleable, resource friendly and fast to
work with. my plone 5 talk (in german) is an example i like :)
http://johannes.raggam.co.at/up-next-plone5/index.html#/


List of missing Patterns
========================

See open tasks for Plone 5 https://github.com/plone/Products.CMFPlone/issues/184


