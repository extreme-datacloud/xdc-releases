EOS
==============

.. contents:: Table of Contents

**EOS** is an open-source storage software solution to manage multi PB storage for the CERN
Large Hadron Collidor LHC. Core of the implementation is the XRootD framework providing a
feature-rich remote access protocol.

Release Notes
-------------

.. toctree::
   :maxdepth: 1
   :glob:

   eos/*

Documentation
-------------

Detailed documentation is available at:

- `EOS - OpenStorage Documentation <https://eos-docs.web.cern.ch/eos-docs/>`_

  - information specific to XDC features can be found under the sections:

    - "Configuration" (setting a Filesystem to use logical path)
    - "Using EOS" (describing the adoption of storage/files process)
    - "Client Commands" (the command to trigger the import [adoption] procedure). 

  - `QoS interface <https://eos-docs.web.cern.ch/eos-docs/configuration/qos.html>`_
  - `Converter Engine <https://eos-docs.web.cern.ch/eos-docs/configuration/converter_engine.html>`_


Deployment automation:
----------------------

**Important note**:

- For packages insallation it is important to enable not only the XDC repositories, through the use of
  the xdc-release-2.0.0-1 package, but also the EOS dependencies repository `eos-deps.repo <https://repo.indigo-datacloud.eu/repository/xdc/repos/eos-deps.repo>`_

Puppet modules are available for:

- EOS server module: https://gitlab.cern.ch/ai/it-puppet-module-eosserver/
- Example files for setting up the namespace node and the storage node:

  - https://gitlab.cern.ch/ai/it-puppet-hostgroup-eos/blob/qa/data/hostgroup/eos/home/i00/ns.yaml
  - https://gitlab.cern.ch/ai/it-puppet-hostgroup-eos/blob/qa/data/hostgroup/eos/home/i00/storage.yaml


Support
-------

- EOS tracking: https://its.cern.ch/jira/projects/EOS/issues/ 

- XDC project’s internal support ticketing system: http://jira.extreme-datacloud.eu/

