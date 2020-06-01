v2.5.0-FINAL
------------

What’s new
~~~~~~~~~~
This version provides some important improvements

List of RfCs
~~~~~~~~~~~~
- New features:

  - Integration with the Data Orchestration System "Rucio"

    - added new dependency: rucio client library
    - added integration with Message Bus (AMQP)

- New API endpoint allows users to register Deployment Triggers
- Implemented a new workflow for supporting the "data pre-processing at ingestion" scenario



Service Dependencies
~~~~~~~~~~~~

The PaaS Orchestrator v.2.5.0-FINAL has the following services dependencies

- CMDB release v0.5, must be populated by CIP 0.10.6
- SLAM release v2.0.0
- CPR release v0.7.0
- Monitoring - Zabbix Wrapper 1.0.2 (docker image indigodatacloud/zabbix-wrapper:indigo_2)

  - Monitoring probes: Openstack probe 1.4.2, Mesos probe 1.4 and QCG probe 1.0

- IM release 1.9.2 
- (Optional) Onedata >= v18.0.2-rc[11,12]
- (Optional) Vault 1.1.2
- tosca-types >= v4.0.0

Installation methods
~~~~~~~~~~~~~~~~~~~~

- for installation instructions please follow the `INDIGO PaaS Orchestator - How to deploy <https://indigo-dc.gitbook.io/indigo-paas-orchestrator/how_to_deploy>`_
- for upgrade instructions please follow the `INDIGO PaaS Orchestator - How to upgrade <https://indigo-dc.gitbook.io/indigo-paas-orchestrator/how_to_upgrade>`_


Known Issues
~~~~~~~~~~~~

- N/A

List of Artifacts
~~~~~~~~~~~~~~~~~
- Docker Container:

  - `indigodatacloud/orchestrator:XDC-2 <https://hub.docker.com/layers/indigodatacloud/orchestrator/XDC-2/images/sha256-150e430bc7672ef0b54e9f849e1f0208da9fed0f7cff5626f379eb6778579772?context=repo>`_(signed)
  - `indigodatacloud/orchestrator:2.5.0-FINAL <https://hub.docker.com/layers/indigodatacloud/orchestrator/2.3.0-final/images/sha256-150e430bc7672ef0b54e9f849e1f0208da9fed0f7cff5626f379eb6778579772?context=repo>`_
