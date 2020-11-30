Working with Elgato Stream Deck
===============================

While Up Deck offers a nice interface, there are those among us whom still
would rather have a hardware deck for their own reasons, well your in luck,
we got you covered.

Up Deck offers a feature, where you can use a HTTP request to trigger the
the button of a deck. this is the ``/xdeck`` url. You can use this on any deck
that has been saved on the server::

    curl http://127.0.0.1:10314/xdeck/deck_name/1

This would cuase the button number 1 to trigger from the deck named
"deck_name".


Normally
--------

You should just be able to configure Stream Decks built in open url, and have
open in the background, however several users, and Elgato Support have confimed
that opening links in the background will cause miss-fires and won't always
trigger. This is a problem with Stream Deck, and has nothing to do with UP Deck

We're not normal
----------------

.. _BarRaider: https://barraider.com/#plugins

Since all we need to do is get anything to open the url up for us, we've found
**API Ninga** from `BarRaider`_ (Find it on the Plugin Store, or their
Discord) and is described as

    Use GET/POST/PUT API commands and see the result on the Stream Deck

Settings:

* Request type: **GET**
* API URL: ``http://127.0.0.1:10314/xdeck/{deck name}/{button number}`` (make
  sure to match the port (10314), deck name, and button number to the values
  you need)
* Content Type: **text/plain**

Just configure it for the button you want, and away you go
