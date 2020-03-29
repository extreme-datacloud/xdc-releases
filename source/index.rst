Welcome to eXtreme-DataCloud releases Documentation
===================================================

You'll find here usefull information regarding the eXtreme-DataCloud
services and components **releases**, their schedules, documentation and
support.

.. contents::

eXtreme-DataCloud releases
--------------------------


.. toctree::
   :maxdepth: 1

   releases/quasar/index.rst
   releases/pulsar/index.rst


Release repositories
--------------------

Source Code repositories
~~~~~~~~~~~~~~~~~~~~~~~~

Source code repositories are available on `GitHub under the "indigo-dc" and "extreme-datacloud" organizations <http://bit.ly/extreme-datacloud>`_

Artefacts repositories
~~~~~~~~~~~~~~~~~~~~~~

eXtreme-DataCloud **production** (stable) `repositories <http://repo.indigo-datacloud.eu/repository/xdc/production/>`_:

* xdc/production/{1,2}/centos7/x86_64/{base|updates}
* xdc/production/{1,2}/ubuntu/{xenial,bionic}/main/
  * containing signed, well tested software components
* third-party:
  * xdc/production/{1,2}/centos7/x86_64/third-party/
  * xdc/production/{1,2}/ubuntu/dists/{xenial,bionic}/third-party
    * containing packages that are not part of eXtreme-DataCloud project, or not part of the base OS or EPEL, but used as dependencies by other eXtreme-DataCloud components

YUM & APT **configuration files** are available `here <http://repo.indigo-datacloud.eu/repository/xdc/repos>`_
or use the **xdc-release** package to install eXtreme-DataCloud repositories

For installation and configuration please follow the **Generic Installation and Configuration Guides**, available for each XDC 
major release.

Release schedule
----------------

* Time-based releases
   - **projects’ Major releases** - the eXtreme-DataCloud project foresees two major releases, distributions, during its lifetime, at around 10 months since the start of the project.
* As-soon-as-available
   - **components’ Minor/Revision releases** - in a project Major release, Development teams (aka Product Teams) can release updated versions of their components as soon as the XDC software quality criteria are met. Thought the project Continuous Integration and Delivery System tests are continuously run giving feedback on the status of the components.

Documentation
-------------

Please find XDC-2 documentation `here <https://releases.extreme-datacloud.eu/>`__.


Support Model
~~~~~~~~~~~~~

-  in a Major Release for each component or service only the latest
   revision released is supported.
-  for each component or service a (major) release is supported at least
   for the lifetime of the projects’ major release in which this version
   was released the first time.

Supported platforms
-------------------

- eXtreme-DataCloud releases are supported on the following platforms:
  
  - CentOS7, Ubuntu 16.04 and 18.04 (only for XDC_2)
  
    - for the products distributed through rpms and deb packages
    
  - all platforms supporting Docker containers
    
    - for the products distributed as docker images

Supported artifacts & packaging formats
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Packages:

   -  Binaries: executable packages
   -  Sources: when available, package files that contain all of the necessary files to compile/build the respective piece of software
   -  Tarballs: clients are distributed as tarballs for all the platforms

- Containers: Docker images are made available for some of the project software

