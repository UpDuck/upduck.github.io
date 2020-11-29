Introduction to buttons
=======================

Buttons are at the heart of what Up Deck does and the can:

* Are part of exactly one deck
* Be edited
* Have custom icons
* Have a highlight
* Have 1, or 2 states
* Be part of a hilite group

There are a lot of buttons, as of the more recent versions you can have up to
500 buttons.

Decks
-----

Decks are simply a grouping of buttons. On the App, only one deck can be
active and its not stored an any particular name. On the HTTP server you can have
many decks and the interfaces will carry the context of which deck you are
currently working with.

You can sync individual button updates with the app if it is connected while
you edit the button.

You can restore any deck from the server onto the App. This will replace
the active deck and restart the App, the buttons previously configured
**WILL NOT** be saved, you need to determine if you want to save the current
deck before performing a restore.

You can save the App's current deck locally or to the server if you are
connected.

Editing buttons
---------------

Editing buttons can be accomplished one of two ways, in the mobile app, or
via the HTTP interface on the desktop. For the mobile app, **to edit a button
simply long press on the desired button to edit it**. On the HTTP interface,
you would navigate to the **Deck Buttons** tab, and select the deck you want
to edit, and then you can click on the button position and the edit interface
will open.

Custom Icons
------------

Each button (and even the second state) can have a custom Icon to represent the
button for your own ease of identification.

Icons can consist of bmp, png, jpeg and gif (it won't animate) files.

Hilite
------

Buttons can have a hilite color wrapped around the outside of a button from
a set of predefined colors. These take on different a different aspect if
the button is dual-state or part of a hilight group (see blow for both).

In the case of a single button, the hilite will always be visible around the
button icon.


Singe and dual-state
--------------------

Buttons can consist of a single state, where if you keep hitting the button
it does the exact same thing. Alternatively they can be a dual-state toggle
style button. In this case, the button remembers which state it was in, and
runs the command for the other state when you hit the button again.

Because of this, dual state buttons can not be part of a hilite group because
the two states are a functionally their own highlight group. This also means
that you can highlight the different states i.e. off/on could highlited
red/green.

Hilite group
------------

Single state buttons can optionally be part of a hilight group, in this case
the last button pressed will have the hilite color visible.

This is useful if you have multiple scene selections and want to visualize
which one is currently active on the deck.
