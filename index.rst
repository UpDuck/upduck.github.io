Welcome to Up Duck's documentation!
===================================

.. note:: this is a documentation site for both UP Deck and Up Duck

.. _Up Deck: http://8up.uk
.. _godot engine: https://godotengine.org/

Up Duck is a re-write of `Up Deck`_ on `godot engine`_. This is done for
various reasons among them:

* Up Deck is written in such a way that makes it hard to extend.
* The mobile app (Corona/Solar2d) and server (Love2d) are written in different engines.

Godot offers some solution to the last one, in that It can target HTML5, Android, iOS, Win, Mac, and Linux all from the same codebase.

Why a game engine? The portability is a large portion, but it also solves some
other ancillary problems, reactive UX and sound. Godot handles the reactive UX
very well and has a large number of builtins that make it easy to provide the
same interface that handles scaling, and porting well, this was lacking from
Love2d, which is likely why the app was written in Solar2d instead. The sound
system while built in in Love2d is also primitive, and without a handful of
third-party plugins it would be difficult to provide as many effects as are
possible out of the box in Godot.

The drawback? Like Love2d, Godot requires a video card, specifically a driver capable of OpenGL ES 2.0. Basically anything from 2008 onward should easily
support this. This functionally should exclude some Virtual Machines (VMs) that
don't offer a fully featured graphics driver (Azure VPS instances appear to fall
in this group), but then again you probably want a graphics chipset to do video
encoding anyway.

Compatibility
-------------

Up through version 1, we will not be modifying anything to make it
fundamentally incompatible with Up Deck. There may be new commands
created, but the deck format, and client/server structure won't be
changed in breaking ways. In this way, you can rely on the docs here
as an add-on to the existing `Up Deck`_ docs. Additionally, we will mark
documents that only apply to **Up Duck**.

.. toctree::
   :maxdepth: 1
   :caption: Tutorials

   updeck/tutorials/getting-started
   updeck/tutorials/troubleshooting
   updeck/tutorials/intro-to-buttons
   updeck/tutorials/intro-to-commands

.. toctree::
   :maxdepth: 1
   :caption: Guides

   updeck/guides/stream-deck
   updeck/guides/moving-outside-the-box

.. toctree::
   :maxdepth: 1
   :caption: Working with commands

   updeck/commands

Indices and tables
==================

* :ref:`genindex`
* :ref:`search`
