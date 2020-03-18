XDC-1 (Pulsar)
==============

The `eXtreme-DataCloud <https://extreme-datacloud.eu/>`__
project is pleased to announce the general availability of its **first
public software release**, codenamed **Pulsar**


Included components
-------------------

.. toctree::
   :maxdepth: 1

   cod 
   dcache
   dynafed
   eos
   fts 
   onedata
   paas-orchestrator
   ttt


Highlights
----------


Key technical highlights:

- CachingOnDemand

  - deployment receipts for geographically distributed caches (via xcache)
  - deployment receipts for scalable local caches (via xcache and http)

- dCache

  - new QoS types integration, aggregated QoS for storage federations
  - OpenIDConnect support in dcache_view
  - dcache storage events (SSE notifications): Allow non-dCache agent 
    to get notified that something of interest happen inside dCache

- Dynafed

  - Integration of OIDC authentication

- EOS

  - Caching with xcache for geographic deployment: Xcache deployed
    at a remote centre to accelerate its local CPU
  - External storage adoption (Through an S3 or a WebDAV interface)
  - External data adoption (Data already present on a system described
    above can be incorporated into EOS)

- FTS & GFAL

  - QoS support: can now accept a QoS job
  - OpenIDConnect support
  - QoS in gfal (gfal with basic cdmi client) – python bindings available

-  PaaS Orchestrator

  - Implementation of Dynafed plugin
  - Interaction via INDIGO IAM OAUTH2 token
  - Enhancement of ONEDATA plugin

- Onedata

  - Performance and stability improvements
  - Support for groups and roles
  - New RADOS driver


Release Notes
-------------

The XDC-1 (Pulsar) release consists in X Products and and a number of technical guides:

-  113 OS packages

   -  100 RPMS & SRPMS, and tarballs
   -  13 binary & source DEBS

-  6 Docker containers

The release is fully supported 
- on the following Operating Systems platforms: 
   - CentOS 7
   - Ubuntu 16.04
   - Optionally PTs support also other OS platforms. You can find more information in the individual
     products documentation.

You can find in the later sections the full list of products, with
detailed release notes and instructions for their
installation/configuration.

Generic Installation Notes
------------------

All eXtreme-DataCloud products are distributed from standard
OperatingSystems (OS) repositories and DockerHub registry.

The packages repositories have the following structure:

* XDC **production** (stable):

  * `xdc/production/1/centos7/x86_64/{base|updates} <http://repo.indigo-datacloud.eu/repository/xdc/production/1/centos7/x86_64/base/repoview/>`_
  * `xdc/production/1/ubuntu/dists/xenial/main/{binary-amd64,source} <http://repo.indigo-datacloud.eu/repository/xdc/production/1/ubuntu/dists/xenial/main/>`_

    * containing signed, well tested software components

  * third-party:

    * `xdc/production/1/centos7/x86_64/third-party <http://repo.indigo-datacloud.eu/repository/xdc/production/1/centos7/x86_64/third-party/repoview>`_
    * `xdc/production/1/ubuntu/dists/xenial/third-party{binary-amd64,source} <http://repo.indigo-datacloud.eu/repository/xdc/production/1/ubuntu/dists/xenial/third-party>`_

      * containing packages that are not part of eXtreme DataCloud, or not part of the base OS or EPEL, but used as dependencies by other eXtreme DataCloud components

* XDC **testing**: `xdc/testing/1/{centos7,ubuntu}/ <http://repo.indigo-datacloud.eu/repository/xdc/testing/>`_

  * containing packages that will become part of the next stable distribution; in the certification and validation phase.

* XDC **preview**: `xdc/preview/1/{centos7,ubuntu}/ <http://repo.indigo-datacloud.eu/repository/xdc/preview/>`_

  * containing signed packages that will become part of the next stable update, available for technical-previews

All signed packages use the INDIGO - DataCloud gpg key. The public
key can be downloaded from
`here <http://repo.indigo-datacloud.eu/repository/RPM-GPG-KEY-indigodc>`_,
and the fingerprint from
`here <http://repo.indigo-datacloud.eu/repository/INDIGODC_key_fingerprint.asc>`_.

It is strongly recommended the use of the lastest version of the
xdc-release packages containing the public key and the YUM and APT
repository files.

On the `DockerHub Registry <https://hub.docker.com/>`_, eXtreme-DataCloud uses the INDIGO - DataCloud and XDC Organizations:

-  `indigodatacloud <https://hub.docker.com/u/indigodatacloud/dashboard/>`_,
   
-  `xdc <https://hub.docker.com/u/extremedatacloud/dashboard/>`_

Containers present in those repositories and released in XDC-1 are
tagged with “XDC-1” tag and signed, leveraging the Docker’s trust
features so that users can pull trusted images.

To understand how to install and configure XDC-1/Pulsar services and
components either refer to the `Generic Installation Notes`_ chapter or to each individual product
documentation.

Software
--------

XDC-1 software can be downloaded from `eXtreme-DataCloud repositories <http://repo.indigo-datacloud.eu/repository/xdc/>`_.

Documentation
-------------

Please find XDC-1 documentation `here <https://releases.extreme-datacloud.eu/>`_.

Support
-------

Most complex software contains bugs, we are not an exception. One of the
features of free and open source software is the ability to report bugs,
helping to fix or improve the software you use.

eXtreme-DataCloud project uses the `INDIGO Catch-All GGUS - Support Unit <https://wiki.egi.eu/wiki/GGUS:INDIGO_DataCloud_Catch-all_FAQ>`_ and
the *support@extreme-datacloud.eu* for general support requests.
More details regarding each product support channels are provided in the
respective products release pages.

Developers, researchers and IT enthusiasts: feel free to write to
info@extreme-datacloud.eu to ask for more information on how to use XDC solutions
for your work. For automatic notifications you can register to the eXtreme-DataCloud release RSS feed or subscribe to the 
eXtreme-DataCloud Announce Mailing list. You can also socialize with us
via `Twitter <https://twitter.com/XtremeDataCloud>`_, Facebook and join our `LinkedIn group <https://www.linkedin.com/groups/12181004/>`_.
