XDC-2 (Quasar)
==============

The `eXtreme-DataCloud <https://extreme-datacloud.eu/>`__
project is pleased to announce the general availability of its **second
public software release**, codenamed **Quasar**


Included components
-------------------

.. toctree::
   :maxdepth: 1

   cod
   dynafed
   eos
   rucio 
   onedata
   paas-orchestrator
   paas-dashboard
   orchent
   ttt


Key technical highlights
------------------------

- CachingOnDemand

  - improved Ansible recipes and new Ansible tasks for Kubernetes and Centos7 baremetal

- Dynafed

  - Dynafed can now function as the active party for data distribution, having enabled the "Fourth party copy" feature. 
    This allows services without third party copy support (such as S3) to participate fully in the data distribution infrastructure.

- EOS

  - Many improvements and features on the QoS classes
    - Addition of QoS classes and QoS API when interacting with namespace entries
    - CDMI gateway for QoS transitions
  - The Converter Driver, part of the Converter Engine, has been reworked using a threadpool approach and saving 
    the information in persistent storage (QuarkDB implementation). This allows persistence, 
    as well as more flexibility over the conversion execution, such 
    as runtime configurable threads and runtime statistics

- Onedata

  - Release of python bindings for onedata in a form of `onedataFS <https://github.com/onedata/fs-onedatafs>`_, allowed to greatly simplify and improve performance of programmatic operations on data located in Onedata space.
  - Improved support of ECRIN and CTA use cases:
    - improvement of file indexing performance for scanning a 800k dataset provided by ECRIN
    - the redesign of the changes stream API, to allow more fine-grained control over the stream

-  PaaS Orchestrator plugin

  - Implementation of timeout for deployment creation/update and credentials management for 
    providers not integrated with IAM
  - Added credentials management for providers not integrated with INDIGO IAM
  - Updated A4C Tosca Parser library (v2.1.0-DEEP-1.2.1)
  - Improved retry strategy for Marathon deployments

-  PaaS Orchestrator Dashboard

  - First release of the **INDIGO PaaS Orchestrator - Simple Graphical UI** allowing users to easly 
    deploy desired workflows and infrastructures

- Rucio

  - The authentication and authorization mechanism was extended to support (JWT) tokens using OpenID Connect protocol
  - Rucio user pre-provisioning (via new Rucio SCIM client) was `implemented <https://github.com/rucio/probes/pull/11>`_ as a ‘Rucio probe’ script

- TOSCA types and templates

  - Added new TOSCA types for BlockStorage, AttachesTo relationship, Elasticsearch and Kibana, 
    while impoving the ones for Kubernetes
  - Updated TOSCA templates to ensure the compliance with Simple Profile in YAML 1.0
  - Added TOSCA templates for the LifeWatch use-case

Release Notes
-------------

The XDC-2 (Quasar) release consists in 9 Products:

-  XXX OS packages

   -  Y RPMS & SRPMS, and tarballs
   -  Z binary & source DEBS

-  7 Docker containers

The release is fully supported 
- on the following Operating Systems platforms: 
  - CentOS 7
  - Ubuntu 16.04 & 18.04
  - Optionally PTs support also other OS platforms. You can find more information in the individual
    products documentation.

You can find in the later sections the full list of products, with
detailed release notes and instructions for their
installation/configuration.

Generic Installation Notes
------------------

All eXtreme-DataCloud products are distributed from standard
Operating Systems (OS) repositories and DockerHub registry.

The packages repositories have the following structure:

* XDC **production** (stable):

  * `xdc/production/2/centos7/x86_64/{base|updates} <http://repo.indigo-datacloud.eu/repository/xdc/production/2/centos7/x86_64/base/repoview/>`_
  * `xdc/production/2/ubuntu/dists/xenial/main/{binary-amd64,source} <http://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/xenial/main/>`_
  * `xdc/production/2/ubuntu/dists/bionic/main/{binary-amd64,source} <http://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/bionic/main/>`_

    * containing signed, well tested software components

  * third-party:

    * `xdc/production/2/centos7/x86_64/third-party <http://repo.indigo-datacloud.eu/repository/xdc/production/2/centos7/x86_64/third-party/repoview>`_
    * `xdc/production/2/ubuntu/dists/xenial/third-party{binary-amd64,source} <http://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/xenial/third-party>`_
    * `xdc/production/2/ubuntu/dists/bionic/third-party{binary-amd64,source} <http://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/bionic/third-party>`_

      * containing packages that are not part of eXtreme DataCloud, or not part of the base OS or EPEL, but used as dependencies by other eXtreme DataCloud components

* XDC **testing**: `xdc/testing/2/{centos7,ubuntu}/ <http://repo.indigo-datacloud.eu/repository/xdc/testing/>`_

  * containing packages that will become part of the next stable distribution; in the certification and validation phase.

* XDC **preview**: `xdc/preview/2/{centos7,ubuntu}/ <http://repo.indigo-datacloud.eu/repository/xdc/preview/>`_

  * containing signed packages that will become part of the next stable update, available for technical-previews

All signed packages use the INDIGO - DataCloud gpg key. The public key can be downloaded from
`here <http://repo.indigo-datacloud.eu/repository/RPM-GPG-KEY-indigodc>`__,
and the fingerprint from
`here <http://repo.indigo-datacloud.eu/repository/INDIGODC_key_fingerprint.asc>`__.

It is strongly recommended the use of the lastest version of the
xdc-release packages containing the public key and the YUM and APT
repository files.

On the `DockerHub Registry <https://hub.docker.com/>`__, eXtreme-DataCloud uses the INDIGO - DataCloud and XDC Organizations:

-  `indigodatacloud <https://hub.docker.com/u/indigodatacloud/dashboard/>`__,
   
-  `xdc <https://hub.docker.com/u/extremedatacloud/dashboard/>`__

Containers present in those repositories and released in XDC-2 are
tagged with “XDC-2” tag and signed, leveraging the Docker’s trust features so that users can pull trusted images.

To understand how to install and configure XDC-1/Pulsar services and
components either refer to the `Generic Installation Notes`_ chapter or to each individual product
documentation.

Software
--------

XDC-2 software can be downloaded from `eXtreme-DataCloud repositories <http://repo.indigo-datacloud.eu/repository/xdc/>`__.

Documentation
-------------

Please find XDC-2 documentation `here <https://releases.extreme-datacloud.eu/>`__.

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
