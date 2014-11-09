---
layout: main
title: about
---

Hi, I'm Phil.
=============

I'm currently an applied physics Ph.D student at Yale working on
superconducting quantum computing under [Rob Schoelkopf](http://www.eng.yale.edu/rslab).
In addition to being a physics enthusiast, I'm also a zealous pythonista and a
fan of the [Qt Project](http://qt-project.org/).

I'd like to use this site to explore web development, document my various
projects, create interactive demonstrations, and write up explanations of
concepts from my field.

Projects
========

## Qt Projects

- [Liveplot](http://github.com/PhilReinhold/liveplot): Visualize and interact
  with array data on the fly
- [H5Explore](http://github.com/PhilReinhold/H5Explore): Explore and plot the
  contents of hdf5 files
- [gui builder](http://github.com/PhilReinhold/pyHFSS): Quickly create GUIs out
  of scripts using a fair bit of magic introspection
- [pyqt utils](http://github.com/PhilReinhold/pyqt_utils): Enhanced widgets for
  scientific qt projects

## Math and Physics

- [pyHFSS](http://github.com/PhilReinhold/pyHFSS): A pythonic interface to
  scripting the Ansoft HFSS application
- [vectfit](http://github.com/PhilReinhold/vectfit_python): A python clone of
  the [vector fitting algorithm](http://www.sintef.no/Projectweb/VECTFIT/) for
  identifying poles in the complex plane
- [brune](http://github.com/PhilReinhold/vectfit_python): *work in progress* A
  python implementation of the the Brune network synthesis algorithm
- [pozar](http://github.com/PhilReinhold/pozar): Conversions between matrix
  representations of electrical networks

Notes
=====

{% for post in site.posts %}
[{{ post.title }}]({{ post.url }})
{% endfor %}
