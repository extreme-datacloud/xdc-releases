vXDC-1
------------

What’s new
~~~~~~~~~~

Upstream corresponding version: v. 5.1.0

New features introduced:

* **Quality of Service**

  * **Users** will interact with this feature using the graphical UI dCache View or through the
    REST API. While switching between QoS levels in dCache View is intuitive, the REST API
    is dynamically documented: all RESTful services have been provided with basic annotations
    in order automatically to generate API documentation. A convenient web interface which
    allows exploration and testing of the API, describing paths, parameters, error codes and
    JSON output, now runs at: [https://[host]:3880/api/v1].
  * **Administrators** will need to set up their pools with tape connection as usual, and the GUI
    and REST interfaces are by default enabled for systems where the administrators choose to
    activate the frontend service.

 
* **Events (Kafka and SSE)**

  * **Users** can listen to the various events sent from a dCache using industry-standard tools
    for the respective messaging systems.
  * **Administrators** need to enable messaging and configure topics and triggers. This will be
    described in detail as soon as the Book is published, on the subpage /kafkaproducer/. In 
    short: Kafka and Zookeeper need to be installed and available for the dCache instance in 
    question, and the following properties need to be configured

  .. code-block:: bash

    (one-of?true|false)dcache.enable.kafka = true
    {{ {{ dcache.kafka.bootstrap-servers = localhost:9092}}}}

List of RfCs
~~~~~~~~~~~~
* N/A

Known Issues
~~~~~~~~~~~~

* None

List of Artifacts
~~~~~~~~~~~~~~~~~
* CentOS-7 RPMS
    * `dcache-5.1.0-1.xdc.noarch.rpm <http://repo.indigo-datacloud.eu/repository/xdc/production/1/centos7/x86_64/base/repoview/dcache.html>`_
    * `dcache-srmclient-5.1.0-1.xdc.noarch.rpm <http://repo.indigo-datacloud.eu/repository/xdc/production/1/centos7/x86_64/base/repoview/dcache-srmclient.html>`_


* Ubuntu 16.04 DEBS
    * 