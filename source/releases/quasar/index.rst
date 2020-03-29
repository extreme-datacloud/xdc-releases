##############
XDC-2 (Quasar)
##############

The `eXtreme-DataCloud <https://extreme-datacloud.eu/>`__
project is pleased to announce the general availability of its **second
public software release**, codenamed **Quasar**


Included components
===================

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
========================

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
-  PaaS Orchestrator

  - Implementation of timeout for deployment creation/update and credentials management for 
    providers not integrated with IAM
  - Added credentials management for providers not integrated with INDIGO IAM
  - Updated A4C Tosca Parser library (v2.1.0-DEEP-1.2.1)
  - Improved retry strategy for Marathon deployments
-  PaaS Orchestrator Dashboard

  - First release of the **INDIGO PaaS Orchestrator - Simple Graphical UI** allowing users to easly deploy desired workflows and infrastructures

- Rucio

  - The authentication and authorization mechanism was extended to support (JWT) tokens using OpenID Connect protocol
  - Rucio user pre-provisioning (via new Rucio SCIM client) was `implemented <https://github.com/rucio/probes/pull/11>`_ as a ‘Rucio probe’ script

- TOSCA types and templates

  - Added new TOSCA types for BlockStorage, AttachesTo relationship, Elasticsearch and Kibana, 
    while impoving the ones for Kubernetes
  - Updated TOSCA templates to ensure the compliance with Simple Profile in YAML 1.0
  - Added TOSCA templates for the LifeWatch use-case

Release Notes
=============

The XDC-2 (Quasar) release consists in 9 Products:
-  77 OS packages

   -  47 RPMS, SRPMS, and tarballs
   -  35 binary & source DEBS

-  8 Docker containers

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
==========================

This chapter provides information on how to enable and use the XDC software repositories 
hosting the second major release XDC-2 (Quasar).

All eXtreme-DataCloud products are distributed from standard Operating Systems (OS) repositories and DockerHub registry.

Installing the Operating Systems
--------------------------------

CentOS 7 
^^^^^^^^

For more information on CentOS please check: [https://www.centos.org/](https://www.centos.org/)

All the information to install this operating system can be found at [https://www.centos.org/download/](https://www.centos.org/download/)

You will find there information on CentOS [packages](http://mirror.centos.org/centos/7/) and [Docker Containers](https://hub.docker.com/_/centos/).

The EPEL repository
"""""""""""""""""""

If not present by default on your nodes, you should enable the EPEL repository (https://fedoraproject.org/wiki/EPEL)

EPEL has an 'epel-release' package that includes gpg keys for package signing and repository information. Installing the latest version of epel-release package available on EPEL7 repositories like:
* [http://download.fedoraproject.org/pub/epel/7/x86_64/e/](http://download.fedoraproject.org/pub/epel/7/x86_64/e/) 

allows you to use normal tools, such as **yum**, to install packages and their dependencies. By default the stable EPEL repo should be enabled.


Ubuntu 16.04 & 18.04
^^^^^^^^^^^^^^^^^^^^

* For more information on Ubuntu please check: [http://www.ubuntu.com/](http://www.ubuntu.com/)

Information to install this operating system can be found at [http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/) and or at [Ubuntu Community Installation Guide ](https://help.ubuntu.com/community/Installation) and regarding Docker Containers at [Ubuntu Official Docker repository](https://hub.docker.com/_/ubuntu/).


Enable the eXtreme - DataCloud packages repositories
----------------------------------------------------

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
`here <http://repo.indigo-datacloud.eu/repository/RPM-GPG-KEY-indigodc>`_,
and the fingerprint from
`here <http://repo.indigo-datacloud.eu/repository/INDIGODC_key_fingerprint.asc>`_.

* for CentOS7 save the key under */etc/pki/rpm-gpg/* 

.. code-block:: bash

    # rpm --import http://repo.indigo-datacloud.eu/repository/RPM-GPG-KEY-indigodc

* for Ubuntu: 

.. code-block:: bash

    # wget -q   -O - http://repo.indigo-datacloud.eu/repository/RPM-GPG-KEY-indigodc | sudo apt-key add -


Giving eXtreme - DataCloud repositories precedence over EPEL
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

It is strongly recommended that INDIGO repositories take precedence over EPEL when installing and upgrading packages.
For manual configuration:
* you must install the **yum-priorities**** plugin and ensure that its configuration file, */etc/yum/pluginconf.d/priorities.conf* is as follows:<br>

.. code-block:: bash

    [ main ]
    enabled = 1
    check_obsoletes = 1

For automatic configuration:
* we strongly recommend the use of **xdc-release** package. Please follow the instructions given bellow on what version of the package to use, how to get and install it.

Configuring the use of eXtreme - DataCloud repositories
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

XDC-2 production repositories are available at:
* http://repo.indigo-datacloud.eu/repository/xdc/

YUM & APT configuration files are available at:
* `CentOS7 repo file <https://repo.indigo-datacloud.eu/repository/xdc/repos/xdc-2.repo>`_
* `Ubuntu 16.04 list file <https://repo.indigo-datacloud.eu/repository/xdc/repos/xdc-2-ubuntu16_04.list>`_
* `Ubuntu 18.04 list file <https://repo.indigo-datacloud.eu/repository/xdc/repos/xdc-2-ubuntu18_04.list>`_

Install repositories :
* CentOS7: 

.. code-block:: bash

    # wget https://repo.indigo-datacloud.eu/repository/xdc/production/2/centos7/x86_64/base/xdc-release-2.0.0-1.el7.noarch.rpm
    # yum localinstall -y xdc-release-2.0.0-1.el7.noarch.rpm 

* Ubuntu 16.04:

.. code-block:: bash

    # wget https://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/xenial/main/binary-amd64/xdc-release_2.0.0-1_amd64.deb
    # dpkg -i xdc-release_2.0.0-1_amd64.deb 

* Ubuntu 18.04:

.. code-block:: bash

    # wget https://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/bionic/main/binary-amd64/xdc-release_2.0.0-1_amd64.deb
    # dpkg -i xdc-release_2.0.0-1_amd64.deb

These packages will install required dependencies, the INDIGO - DataCloud public key and 
ensures the precedence of eXtreme - DataCloud repositories over EPEL and Ubuntu. 

It is strongly recommended the use of the lastest version of the
**xdc-release** packages containing the public key and the YUM and APT
repository files.

Enable the INDIGO - DataCloud Containers repositories
-----------------------------------------------------

On the `DockerHub Registry <https://hub.docker.com/>`_, eXtreme-DataCloud uses the INDIGO - DataCloud and XDC Organizations:

-  `indigodatacloud <https://hub.docker.com/u/indigodatacloud/>`_,
-  `xdc <https://hub.docker.com/u/extremedatacloud/>`_

Containers present in those repositories and released in XDC-2 are
tagged with “XDC-2” tag and signed, leveraging the Docker’s trust features so that 
users can pull trusted images.

Currently, content trust is disabled by default. You must enable it by setting the **DOCKER_CONTENT_TRUST** environment variable, like bellow:

.. code-block:: bash

    # export DOCKER_CONTENT_TRUST=1

For more details regarding the "Content Trust in Docker" please read [Docker's Documentation](https://docs.docker.com/engine/security/trust/content_trust/)

Content trust is associated with the TAG portion of an image.
For XDC-2 (Quasar) release the signed tag is ***XDC-2***. See example bellow if you want to ensure the correct use of eXtreme - DataCloud images:
* for Core Services

.. code-block:: bash

    # export DOCKER_CONTENT_TRUST=1
    # docker pull indigodatacloud/orchestrator:2.3.0-FINAL
    No trust data for 2.3.0-FINAL
    # docker pull indigodatacloud/orchestrator:XDC-2
    Pull (1 of 1): indigodatacloud/orchestrator:XDC-2@sha256:150e430bc7672ef0b54e9f849e1f0208da9fed0f7cff5626f379eb6778579772
    sha256:150e430bc7672ef0b54e9f849e1f0208da9fed0f7cff5626f379eb6778579772: Pulling from indigodatacloud/orchestrator
    93857f76ae30: Pull complete
    [...]
    e8c92b40b492: Pull complete
    Digest: sha256:150e430bc7672ef0b54e9f849e1f0208da9fed0f7cff5626f379eb6778579772
    Status: Downloaded newer image for indigodatacloud/orchestrator@sha256:150e430bc7672ef0b54e9f849e1f0208da9fed0f7cff5626f379eb6778579772
    Tagging indigodatacloud/orchestrator@sha256:441c8b037684422ccdf2fdec322c9c09904ed3ce74d9fcc7d2862a9f53ad36be as indigodatacloud/orchestrator:indigo_2
    # docker images
    REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
    indigodatacloud/orchestrator   XDC-2              bdbe758d9f32        37 hours ago        843MB

* for Applications:

.. code-block:: bash

    # export DOCKER_CONTENT_TRUST=1
    # docker pull extremedatacloud/xdc_lfw_frontend:latest
    No trust data for latest
    # docker pull extremedatacloud/xdc_lfw_frontend:XDC-2
    Pull (1 of 1): extremedatacloud/xdc_lfw_frontend:XDC-2@sha256:dd6024ee2fa9065d5ed332adb7133c582aa93d53b5148bc890079a78f66a63cf
    sha256:dd6024ee2fa9065d5ed332adb7133c582aa93d53b5148bc890079a78f66a63cf: Pulling from extremedatacloud/xdc_lfw_frontend
    [...]
    Digest: sha256:dd6024ee2fa9065d5ed332adb7133c582aa93d53b5148bc890079a78f66a63cf
    Status: Downloaded newer image for extremedatacloud/xdc_lfw_frontend@sha256:dd6024ee2fa9065d5ed332adb7133c582aa93d53b5148bc890079a78f66a63cf
    Tagging extremedatacloud/xdc_lfw_frontend@sha256:dd6024ee2fa9065d5ed332adb7133c582aa93d53b5148bc890079a78f66a63cf as extremedatacloud/xdc_lfw_frontend:XDC-2
    docker.io/extremedatacloud/xdc_lfw_frontend:XDC-2
    # docker images |grep xdc_lfw_frontend
    extremedatacloud/xdc_lfw_frontend                XDC-2               b72acc7380d4        2 weeks ago         4.53GB

Important note on automatic updates 
===================================

The CentOS and Ubuntu Operating Systems both offer auto-updates mechanisms. Sometimes middleware updates require non-trivial configuration changes or a reconfiguration of the service. This could involve service restarts, new configuration files, etc, which makes it difficult to ensure that automatic updates will not break a service. Thus

**WE STRONGLY RECOMMEND NOT TO USE AUTOMATIC UPDATE PROCEDURE OF ANY KIND**

on the eXtreme - DataCloud  repositories (you can keep it turned on for the OS). You should read the update information provides by each service and do the upgrade manually when an update has been released! 

Support
=======

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
