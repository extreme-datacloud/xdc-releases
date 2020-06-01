vXDC-2
------------

What’s new
~~~~~~~~~~

Upstream corresponding version: v. 6.1.3

**Highlights**

- dCacheView: uses inotify-over-SSE to keep page up-to-date.
- storage-events: 

  - added missing events in inotify-over-SSE.
  - performance and robustness improvements for inotify-over-SSE 

- Optional TLS for p2p transfers
- Zone-aware cell messaging
- New serialization format


**Incompatibilities**

- Starting release 6.1 the **BerkeleyDBMetaDataRepository** is the default metadata 
  repository for the pools. Sites that was not explicitly specifying **pool.plugins.meta**
  property have to set the old default value: **pool.plugins.meta=org.dcache.pool.repository.meta.file.FileMetaDataRepository**

- Pool in 6.1.x are not compatible with older dcap doors. However, new dcap doors can 
  operate with existing pools.


List of RfCs
~~~~~~~~~~~~

**Release 6.1**

- cleaner: can delay garbage-collection of deleted data
- dCacheView: uses inotify-over-SSE to keep page up-to-date.
- ftp: 

  - added anonymous FTP support
  - added FTP-with-StartTLS (FTPS) support

- messaging: 

  - services prefer zone-local services when making internal requests.
  - added experimental high-performance serialiser.

- namespace: 

  - remove unnecessary DB operations on file creation.
  - fixed operation with read-only database connections.
    
- poolmanager: 

  - added support for dynamic pool groups
    
- pools: 

  - added support for zones.
  - can now garbage-collect additional capacity under space pressure.

- security: 

  - added support for clients presenting SciTokens
    
- storage-events: 

  - added open/read/write/close events in inotify-over-SSE.
    
- xrootd: 

  - added support for third-party copy (xrootd-TPC)
  - added support for request signing


Known Issues
~~~~~~~~~~~~

* None


Documentation
~~~~~~~~~~~~~

- Upgrade information:

  - https://www.dcache.org/downloads/1.9/release-notes-6.1.shtml
  - https://www.dcache.org/downloads/1.9/release-notes-6.0.shtml
  - https://www.dcache.org/downloads/1.9/release-notes-5.2.shtml
  - https://www.dcache.org/downloads/1.9/release-notes-5.1.shtml
        
- General documentation: https://www.dcache.org/manuals/

  - Userguide (6.1): https://www.dcache.org/manuals/UserGuide-6.1/
  - Admin guide (6.1): https://www.dcache.org/manuals/Book-6.1/



List of Artifacts
~~~~~~~~~~~~~~~~~

- CentOS-7 RPMS

  - `dcache-6.1.3-1.xdc.noarch.rpm <https://repo.indigo-datacloud.eu/repository/xdc/production/2/centos7/x86_64/updates/repoview/dcache.html>`_

- Ubuntu 16.04 DEBS

  - `dcache_6.1.3-1_all.deb <https://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/xenial-updates/main/binary-amd64/dcache_6.1.3-1_all.deb>`_ 

- Ubuntu 18.04 DEBS

  - `dcache_6.1.3-1_all.deb <https://repo.indigo-datacloud.eu/repository/xdc/production/2/ubuntu/dists/xenial-updates/main/binary-amd64/dcache_6.1.3-1_all.deb>`_