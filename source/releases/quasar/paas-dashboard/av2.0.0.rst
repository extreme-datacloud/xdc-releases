v.2.0.0
-------

What’s new
~~~~~~~~~~

The new  PaaS Orchestrator Dashboard is now stateful, storing statsu information in a MySQL DB. This involves many new features and improvements as detailed bellow.

List of RfCs
~~~~~~~~~~~~

- New features:

  - Database connection for storing the application state, i.e. information about the users and their deployments
  - New views for dashboard administrator(s)
  - New functionalities:

    - send notification to users when the deployment is ready
    - generate/store ssh keys (requires that Vault integration is enabled)

  - New operations and views for deployment management: deployment update, deployment extra information
  - New endpoint /info to get dashboard version

- Improvements:

  - Code restructured with the introduction of blueprints for users, deployments, providers, vault, etc.
  - Improved configuration management to make customizations easier:

    - ready-to-use profiles for existing use-cases (deep, xdc, recas, infn-cloud)
    - templates and parameters can be easily overwritten for custom profile

  - Improved Vault integration
  - Improved support for different types of deployment, including HPC jobs (QCG)

Known Issues
~~~~~~~~~~~~

- N/A

Installation methods
~~~~~~~~~~~~~~~~~~~~

- automatic deployment by using the Docker image

  - See documentation at: `PaaS Orchestrator Dashboard README <https://github.com/indigo-dc/orchestrator-dashboard/blob/v2.0.0/README.md>`_

- Services Dependencies

  - Orchestrator >= v2.4.0
  - (Optional) Vault 1.1.2


List of Artifacts
~~~~~~~~~~~~~~~~~

- Docker image:

  - `orchestrator-dashboard:XDC-2 (signed) <https://hub.docker.com/layers/indigodatacloud/orchestrator-dashboard/XDC-2/images/sha256-d80e6b1ae962ad0f548087a09a7a0970232f4e9ca2b2660364ab562f8ed26a48?context=repo>`_
  - `orchestrator-dashboard:v2.0.0 <https://hub.docker.com/layers/indigodatacloud/orchestrator-dashboard/v1.1.0/images/sha256-6fcda9f1c81aec920e0e05d817e11a64284d49597bfe5d1e86e69a9e0522f009?context=explore>`_
