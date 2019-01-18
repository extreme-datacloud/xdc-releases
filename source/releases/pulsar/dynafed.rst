Dynafed
==============

.. contents:: Table of Contents

The **Dynamic Federations system** allows to expose via HTTP and WebDAV a very fast dynamic name
space, built on the fly by merging and caching (in memory) metadata items taken from a number of
(remote) endpoints.

One of its fundamental features is to be redirect GET/PUT requests to the site or cluster
hosting the requested file that is closer to the client that requested it. The focus is on
performance, scalability and realtime fault resilience with respect to sites that can go
offline.

From the perspective of a normal user, HTTP and WebDAV clients can browse the Dynamic Federation
as if it were a unique partially cached name space, which is able to redirect them to the right
host when they ask for a file replica. Dynafed also supports writing. [`more <http://lcgdm.web.cern.ch/dynafed-dynamic-federation-project>`_]

Release Notes
-------------

.. toctree::
   :maxdepth: 1
   :glob:

   dynafed/*

Documentation
-------------
Detailed documentation is available at:

* `Dynafed - The Dynamic Federation project <http://lcgdm.web.cern.ch/dynafed-dynamic-federation-project>`_

Support
-------

* through `GGUS <https://ggus.eu/>`_ by using the `Dynafed Development <https://wiki.egi.eu/wiki/GGUS:Dynafed_Development_FAQ>`_ Support Unit
* Dynafed User Forum mailing-list: dynafed-users-forum (cern.ch)
* XDC project’s internal support ticketing system: http://jira.extreme-datacloud.eu/