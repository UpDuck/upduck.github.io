Getting Started
===============

UP Deck is comprised of three components in order to do its thing:

* Mobile App
* UP Deck Server
* OBS Lua script

Mobile App
----------

The mobile app is the preferred interface for working with your deck.
Android and iOS versions are available on their respective stores.

UP Deck server
--------------

.. _love2d: https://love2d.org/

UP Deck Server is a lua application written on top of the `love2d`_ engine,
this allows the server to be portable to Windows, macOS and Linux

.. note:: A GPU Driver Capable of OpenGL ES 2.0 is required

Windows and macOS
_________________

For Windows and macOS, simply `download the desktop app <download app>`_ and use the installer to
set up both the server and install love2d if it's not already.

Linux
_____

For Linux `download the desktop app <download app>`_ and use your distribution's installer to
install a version of `love2d`_::

    # apt-get install love

You can launch the app via the CLI::

    $ love UPDeck_xxx.love


OBS Lua script
--------------

You can `Download the OBS lua script <download obs>`_ and save it just about anywhere. To
install it simply Launch OBS and go to :menuselection:`Tools --> Scripts`
and use the ( **+** ) to add the script.

.. warning:: Set the message path. OBS will not respond with out it.

.. note:: Some times the script is not copied or configured when creating a new
   Scene Collection in OBS, this appears to be an OBS bug, check your message
   path is still configured after creating a new Scene Collection.

The only important attribute here is the **Message Path** it needs to be set
to the folder that the UP Deck server is running from.

.. note:: On Linux it may be necessary to link ``libobs.so`` and ``libobs.so.1``

Message Path
____________


The message path is used by both OBS and the UP Deck Server to communicate
with each other using files at this path. The path on the server side can not
be modified.

You can quickly find the path by double clicking on the UP Deck Server body
while its running and save the **Settings** page, this will copy the path to
your clipboard.

If you still can't find the message path it will vary depending on your
operating system

**Known Problems**:

* It's been reported that paths that contain extended characters may not work,
  this is likely due to the version of lua built into OBS as it may not support
  characters beyond the standard ascii table.
* If you run OBS as an administrator on Windows, you may find it necessary to
  run UP Deck as an administrator as well. (UP Deck generally does not need to
  be run as Administrator)

Windows
+++++++

Open the windows menu and type in::

    %appdata%\UPDeck\

Then copy and paste the resolved path from explorer into the
**Message Path** (it should look like
``C:\Users\YOURUSERNAME\AppData\Roaming\UPDeck)``

macOS
+++++

On macOS you can type into a shell::

    open "~/Library/Application Support/LOVE/UPDeck/"

And copy and paste the resolved path from finder (it should look like
``/Users/user/Library/Application Support/LOVE/UPDeck/``)

Linux
+++++

On linux you can echo the resolved path::

    $ echo "${HOME}/.local/share/love/UPDeck"

Then copy and paste the resolved path into the **Message Path** (it should look like ``/home/username/.local/share/love/UPDeck``)

More Reading
------------

You can read more on the Up Deck website for info around getting familiar with
the Apps:

.. _download app: https://8up.uk/docs/Download_the_UPDeck_desktop_app
.. _download obs: https://8up.uk/docs/Download_the_OBS_lua_script
.. _download mobile: https://8up.uk/docs/Download_the_mobile_app
.. _app nav:  https://8up.uk/docs/Navigating_around_the_mobile_app

* `Download the desktop app <download app>`_
* `Download the OBS lua script <download obs>`_
* `Download the mobile app <download mobile>`_
* `Navigating around the mobile app <app nav>`_
