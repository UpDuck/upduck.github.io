Moving outside the box
**********************

Security Prefix
===============

UP Deck, while well intentioned is not secure.

# Communications are over plain text TCP
# The password is barely obfuscated
# Commands are not allow-listed, the client can do whatever it wants to do that has an exposed interface
# The HTTP server is custom-built and isn't as robust as common HTTP servers
# There are interfaces for, spawning processes, calling remote URLs, and killing others.

Someone could, if they where so determined and had access, write commands to download data from the internet and launch it. A security minded person, would rightfully consider this as a remote code execution (RCE) exploit waiting to happen.

This risk is currently greatly limited by the environment and implementation:

* the client uses an custom TCP protocol that requires specific knowledge to
  take advantage of.
* HTTP server even if exposed can only edit decks and can not run them.
* Expectation that the user is operating on a private WiFi network (although
  plenty of IoT things are compromised on them)

The gives an overall low risk from Up Deck. However the moment the HTTP server can also remotely trigger buttons, then its a medium trending towards high. If you then turn around and make that interface directly available on the internet (like by forwarding the port on your router) that risk becomes very high.

    If you then turn around and make that interface directly available
    on the internet (like by forwarding the port on your router) that risk
    becomes very high.

Why does HTTP increase this risk so much? HTTP is a well known, and is an easy to walk protocol, it provides rapid feedback to an actor and as such, much of the tools for exploiting the internet are based these easy exploit methods.

Care would need to be taken in exposing the execute side of the deck, and even more care should be taken if you take the non-recommended course of exposing it to the internet.


Reducing Risk
=============

The lecture above aside, steps can be taken to reduce risk if you still want
to go down this path (and there are valid reasons to do so) We'd propose that
you take the following into account (using nomenclature from :rfc:`2119`):


Client App
----------

The client app interface uses a dedicated port (default: 4445) to communicate
over a raw TCP connection in clear text (unencrypted). Data exchanged over
this interface will be processed by the server without question.

* The interface MUST be password protected if you are extending its scope
* The interface MUST NOT be exposed to the public internet
* The interface SHOULD NOT be expanded beyond the local network

  * In the off chance you think this is important you MUST do this over
    encrypted tunneling (VPN).

HTTP Server
-----------

The http server has various urls that have different sensitivity, they can be
classified as **config**, **edit**, and **execute**, which have different risks.

* The HTTP Server MUST NOT be generically exposed to the internet.

Config
++++++

The config urls, including ``/, /setup,`` are very sensitive and MUST NOT be
exposed. As they can change ports, passwords and lock users out.

Edit
++++

The **edit** urls including ``/deck, /schedule`` are used to configure decks,
or setup reoccurring commands.

* The **edit** interface MUST be password protected to prevent un-authorized
  modification
* The edit** interface SHOULD be segregated (with at least a separate password)
  from the **setup**
* The **edit** interface SHOULD be segregated from the **execute** interface
* The **edit** interface SHOULD NOT be exposed to the public internet
* * The **edit** interface SHOULD be exposed over TLS

Execute
+++++++

The **execute** urls, including ``/xdeck/, /live, /liveDeck`` are used to
provide an interface to executing existing decks. Given careful construction
of decks and access to them, the risk can become very minimal.

Each of the urls has a path parmater to the deck in use, this can be useful
in configuring access controls to only specific decks::

    /xdeck/{deck}/{buttonNumber}
    /live/{deck}/...
    /liveDeck/{deck}/...

* The **execute** interface MAY be exposed to the internet

  * The **execute** interface SHOULD be restricted by access control function
    (password, IP allow list, etc...)
  * The **execute** interface SHOULD be restricted to specific decks
  * The **execute** interface SHOULD be exposed over TLS

Options to expose your decks
============================

Exposing one of the **execute** urls should be relatively straightforward for
the running a HTTP service on the internet.

You will need to set up a more mature HTTP server as a proxy to handle
traffic before it gets sent to UP Deck.

A good proxy will allow you you:

* Terminate TLS traffic
* Apply simple access controls to paths
* Rewrite paths if you desire
* Access logs

This gives you a flow like

Internet --> Your Router --> proxy --> UP Deck HTTP

There are a myriad of tutorials on the internet for setting up a home http proxy for your webserver.

Some reccomended proxies are:

* Nginix - this guy powers a large portion of the internet. Its a little more
  complex, but it does everything
* Node - this can be done as a simple proxy wrapper, not much feature wise
  but if you already have node and are only on a private network, its fine
* python http.server - another simple one, would be fine for private networks
