Introduction to commands
========================

Commands are what we use to tell UP Deck or OBS what to do, and how we want
it done.

All command blocks are structured the same they contain a comment line, a
command word, and a number of named and/or positional arguments.

::

  this is the comment line
  show
  scene=this_scene
  val=*

This would toggle the visibility of the scene, this_scene.

Multiple Commands in one button
-------------------------------

A button can contain 1 or more commands. this is accomplished by seperating
each command block with a empty line

::

  this is the first command comment
  show
  scene=this_scene
  val=*

  this is the second command comment
  openurl
  url=http://127.0.0.1:10314/xdeck/deck/1

Variables
---------

Its possible to set, and read variables in your commands. the
:command:`setvar` is the primary way to set a number of variables. Variables
can be read by prefixing them with the ``$`` symbol.

.. note:: Variables are local to the trigger point, if you trigger it on the app
   it will not be defined on the Server (xdeck) and vise-verse.

::

  setup some variables
  setvar
  target=mellon

  switch to the target variable
  switch
  scene=$target

Math Expressions
-----------------

.. _corona math: https://docs.coronalabs.com/api/library/math/index.html

Its possible to evaluate math expressions ``() % < > + - / *`` as well as
functions listed in the `Corona Labs math library <corona math>`_. (with out
the ``math.`` prefix) These expressions can be evaluated
**anywhere** that the encasing square brackets (``[]``) occur.

.. warning:: because of this feature do not use square brackets for any other
   reason in your command blocks

.. note:: just like variables, expressions only evaluate where they
   are triggered and don't synchronize with other apps or the server.

::

  Add 5 to the current value
  setvar
  this_counter=[$this_counter + 5]

Looping
-------

the :command:`loop` is a special command that causes the remaining command
blocks to be executed multiple times

.. note:: looping only works when triggered from inside the app

.. _looping: https://8up.uk/docs/Using_repeat_loops_in_buttons

See more about `looping in the UP Deck docs <looping>`_
