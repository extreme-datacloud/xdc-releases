vXDC-1
------------

What’s new
~~~~~~~~~~

Upstream corresponding version: v. 5.1.0

**Highlights**

* dCache now supports Java 11 as its platform

* Documentation, especially the dCache Book, received a major revision
  and will remain in focus
* HTTP 3rd-party-copying has matured to a feature-rich, well tested state
* Pinboard includes timestamps
* updated external dependencies

**Incompatibilities**

* This release breaks compatibility with pools running dcache version 3.2 or earlier.

**Acknowledgments**

* We thank HTW Berlin students Marcel Munce, Ferdinand Wolff and MaKrHTW (???) as well as Onno Zweers from surfSARA for their contributions.

**Release 5.0.0**

* **Admin**

  * A new property in the *frontend frontend.authz.unlimited-operation-visibility* now controls
    visibility of operations exposing file metadata. The default is
    *false*, meaning non-admin users can only see file operations for
    files which they own or which are anonymous. Setting it to *true*
    allows everyone access. (`267d937c79 <https://github.com/dCache/dcache/commit/267d937c79713330ae2161dd28b05ee4166d2934>`_).
  * Monitoring information exposed through the HTTP GET method is now
    available to all users and not only admin role users. (`32597dc77a <https://github.com/dCache/dcache/commit/32597dc77aeca34144a374e75ffe23e6b3b69a36>`_).
  * The admin data fields like the lists of pools, groups, units, etc.,
    are now sorted by default for the admin REST API. (`4928eff71d <https://github.com/dCache/dcache/commit/4928eff71dabcc66deb3ad35a3a652ce9e1f943c>`_).
  * The dCache admin ssh server now supports kerberos as an authentication
    mechanism (along with password and publickey).
  * `cbab40a841 <https://github.com/dCache/dcache/commit/cbab40a8415e81d96dfd775a0d28f3f9158d2eaf>`_ 
    added the following property to configure admin ssh server authentication:

  .. code-block:: bash

     (any-of?kerberos|password|publickey)admin.ssh.authn.enabled = password,publickey

The keytab's location can be set under

  .. code-block:: bash 

     admin.ssh.authn.kerberos.keytab-file = /etc/krb5.keytab

* **Alarms**

  * A bug impeding reception of email alarms when the XML database is used
    has been fixed.

* **DCAP**

  * Improved features: when using dcap URL to create a file or a directory,
    they are created with dcap get desired file permissions.

* **Frontend**

  * dCache now supports more scientific file formats: HDF4 and 5 files as
    well as ROOT files are now identified and treated as such.
  * The new configuration property *(one-of?true|false)dcache.enable.authn.anonymous-fallback-on-failed-login = true*
    allows modifying the behaviour of the frontend in case of failed logins:
    dCache has a hard-coded "feature" where a user providing bad authentication
    (e.g., wrong password, expired OIDC access-token or macaroon) is treated
    as the anonymous user. This has proved counter-intuitive, as wrong/expired
    credentials often appear to succeed for some operations (e.g., directory
    listing), while failing others (upload/download). Providing the new
    property allows to set a fail-fast behaviour in those cases, providing a
    quicker response to users.
  * To support inotify events, a new plugin for SSE is introduced. Clients
    can discover changes in dCache namespace using an interface modelled after
    the inotify(7) API (See dCache book for detail).
  * dCache View is updated to a new version (v1.5), see dcache-view repository for new feature details.

* **FTP**

  * Bug which have been fixed:

    * The leaking server sockets issue , when a client aborts a proxied
      transfers with kafka ebnabled is now fixed. No further server sockets
      leaked when a proxy is being used, Kafka notification is enabled, and
      the client aborts the transfer.

  * Improved features: Improve date value formatting when sending billing
    events via Kafka.

* **gplazma**

  * The credential information (e.g., distinguished name) is now logged for
    x509 certification chain validation and FQAN extraction failures. (`9c39e149e0 <https://github.com/dCache/dcache/commit/9c39e149e0db31a088d46ebd602fe5fd63c20eb9>`_).
  * Large numerical value gids may be used to define roles fro groupid (gid). (`11b34011ae <https://github.com/dCache/dcache/commit/11b34011ae9c613db6aae0ca8a822853d2cf7e2a>`_).
  * Wildcard match of FQANS is possible for the VO group (vo-group.json) 
    gplazma plugin. (`173dca3a96 <https://github.com/dCache/dcache/commit/173dca3a96d52acca73bac1c9ea568338095037f>`_).
  * A new role, "observer", is defined and available for according 
    read-only access to system or file information. (`4aa440ab2a <https://github.com/dCache/dcache/commit/4aa440ab2abd46cd1903384d2c47ecec0677eb98>`_).
  * The Storage AuthzDB file format is updated to accept an optional
    'max-upload=<value>' element after the 'read-write' or 'read-only' value.
    The label is optional. If present, the value describes the maximum file
    size the user can upload. (`e3dce67083 <https://github.com/dCache/dcache/commit/e3dce67083166451be67c42700640eaed2597669>`_)
  * As some newer authentication mechanisms embed usage limitations; 
    i.e., a user may authenticate in a way that limits what that user can do 
    (E.g. SciTokens) New authentication plugins have the possibility to 
    specify a Restriction as part of the authentication process. Existing 
    authentication plugins are supported as before. (`204024b9e8 <https://github.com/dCache/dcache/commit/204024b9e878b85fbd6a5583908ccada4396d944>`_).
  * A new configuration option has been introduced to capture all information
    about an OpenID-Connect provider, which is some external service that 
    dCache users can authenticate against. This configuration property is a map.
    Each entry of the map associates a nickname with information about that
    provider. The nickname is used when logging problems with the provider.
    The information is the URI of the issuer endpoint. This must be a valid
    URL that starts 'https://'.(`bab4e635ac <https://github.com/dCache/dcache/commit/bab4e635ac1b451b772badc70c9b89da6892ac65>`_).

    * The following example associates the nickname 'google' with Google's
      issuer endpoint.

    .. code-block:: bash

       {{ gplazma.oidc.provider!google = https://accounts.google.com/}}

* **History**

  * Error handling in the history service was improved.

* **Info**

  * The info service now publishes the time that information was collected
    along with the actual data. The timestamp is available via the last-updated
    attribute.
  * Info clients (such as info-provider and storage-report) are now informed
    of the number of files stored in a space reservation.

* **NFS**

  * When pNFS client uses flex_file layout IO errors with pool (data server)
    are reported to NFS door. The erros can be interpreted as:

  .. code-block:: bash
 
     {{ NFS4ERR_NXIO: The client was unable to establish any communication with the storage device.

     NFS4ERR_*: The client was able to establish communication with the storage
     device and is returning one of the allowed error codes.}}

* **PNFS Manager**

  * A user with a macaroon that authorises them to upload data into a
    particular directory will now also be able to create parent directories
    to achieve uploading the data.
  * A bug that prevented get file checksum from working in some cases was fixed.

* **Pool**

  * Fixed pool repository space accounting leak on failed restores from tape (`815ce3eb6a <https://github.com/dCache/dcache/commit/815ce3eb6a7898152d38abd97590336d434545c7>`_).
  * Added Cross-Origin Resource Sharing (CORS) support for HTTP requests (`049c87a814 <https://github.com/dCache/dcache/commit/049c87a8141e3dad7f42f2a2497f01c5db080da9>`_) required by dCacheView.
  * Fixed HTTPS redirected transfers by returning pool canonical hostname in the redirected URLs. (`7f81b8e79d <https://github.com/dCache/dcache/commit/7f81b8e79de9de53545b23ef4fd93448bb17eb3c>`_).
  * Fixed stopwath error to ensure that IO-statistics collecting is more robust, avoiding stack-traces with the
    message 'This stopwatch is already stopped' (`86ede8a240 <https://github.com/dCache/dcache/commit/86ede8a2403598d9b9383e7ebb2a120a3eed7aeb>`_ ).
  * Better handling of HTTP 3-rd party transfers - improved logging of exceptions (`a98d667c16 <https://github.com/dCache/dcache/commit/a98d667c16b2dbff774d0ca91d741de80bb02d9c>`_),
  * increased socket timeout for GET requests (845cfe0bda). 
  * Improved error logging in billing by using exception calss name if exception has null message (24de520285).
  * Removed stack-trace logging of checked exceptions on P2P failures (7a570355fa).
  * Fixed pool runtime configured size regression (f5ba0103ea). 
  * Updated HTTP 3-rd party copy to support retrying GET and HEAD requests for better ineroperability with DPM (d0a621c775).
  * Updated FTP mover to log additional information if it detects partial transfers (e725f7b9e7).
  * Dropped subject from StorageInfoMessage (0e60cdcaaa). 
  * Fixed regression when restoring files from tape (7cdcf4e0a7).
  * Fixed NullPointerException on flush when using Kafka to collect billing records (4e396b9234). 
  * Fixed protocol movers to handle out of disk/out of capacity eerrors.
  * Added support for Content-MD5 request header (4d954e6b5f).
  * Updated HTTP mover to report errors as HTTP status message phrase so that clients that log the status line now provide their users
    with more detailed information about what caused a transfer to fail (6fcaeca34c).
  * Fixed regression that broke "dcache pool convert2 command (`80461b2f9a <https://github.com/dCache/dcache/commit/80461b2f9ad3f881b228b6ce8c3a0857556d9220>`_)
    and "dcache pool convert" command (`80461b2f9a <https://github.com/dCache/dcache/commit/011b3b243972c574f6002062684f0b4cc432a43f>`_).
  * Introduced a retry loop to retry file attributes update in timeout to pnfs manager ([8c60877527]((https://github.com/dCache/dcache/commit/8c60877527869095acf23dd95f424d1df1e5b790).

* **Pool Manager**

  * Select Read Pool requests for which the user does not have enough
    permissions now do not affect other requests any more.
  * Several smaller bugfixes for Pool Manager also went into this release.

* **Resilience**

  * Bugs which have been fixed:
    * an error is no longer reported when trying to handle a broken file which has already been unlinked;
    * the entire pool scan no longer fails when one file in the list is not resilient or has no
    locations;
    * filters referencing invalid pool names no longer cause scan cancel to fail.
  * Improved features:
    * command retry errors immediately reprocesses the most recent failed file operations;
    * the command pool ls now displays the number of file operation errors encountered during a given scan;
    * the list of pools is now sorted by STATE (RUNNING, WAITING, IDLE) and then by pool name in ascending lexicographic order;
    * the inaccessible command now has options to check the status of the job, to display the current
      contents of the 'inaccessible list' file for that pool, and to clean up/delete that file;
    * 'referring pool' has been added to the inaccessible alarm to enable grep'ing the resilience log for a given
      scanned pool.

* **SRM / SRM Manager**

  * Fixes in gridsite delegation storage handling - fixed querying validity
    of delegated credential stored on the gridsite end-point allowing clients
    like davix-cp to work (839604e45f) with dCache;
  * fixed handling of delegated credential with VOMS AC that expires before the X.509 (54658383d1); 
  * imporved error reporting (41976be12d); 
  * added add gridsite delegation interface access-log (5392271fcf).
  * SRM client has been updated to support X509_CERT_DIR environmental variable (ed8b86e604).
  * Fixed handling of duplicate SURLs by SRM client (36b9e0c7d6).

* **WebDAV**

  * A lot of work has gone into making 3rd party copying functionality more robust and scalable.

* **XRootD**

  * Third-party copy was introduced in 4.2, and continues to be improved.
    For further information on configuration, please refer to the documentation in The Book (5.0).
  * Bug fixes and improvements:
  
    * the correct error (kXR_NoSpace) is now returned to the client when there is no more disk space;
    * xrootd now fails fast if the MaxUploadSize is supplied, and the file is too large;
    * the xrootd door spring configuration no longer fails to load when kafka is not activated;
    * the 'stat' request now supports both open file handles as well as paths, enabling use of the --zip option;
    * dCache no longer logs a stack trace when a client requests a file be created, the parent directory does not exist, and the make parent option is omitted;
    * a source path containing a query part on a mv request no longer causes the request to fail;
    * a potential race condition preventing directory listing now is correctly handled;
    * support for the 'tpc' query on the pools has been added in order to comply with the newer (4.9) XrootD clients;
    * it is now no longer necessary nor correct to list 'access-log' among the xrootd plugins; this log handler is added 
      automatically as it is for other doors; (10) file handles and query strings are now included in the access log information;
    * logging of failed authentication is improved to include more useful information, like the DN;
    * it is now possible to identify all entries in the access-log from the same TCP connection via a session identifier.

Known Issues
~~~~~~~~~~~~

* None


Documentation
~~~~~~~~~~~~~

Please find bellow notes on how to enable and exploit the new features introduced in this verions:

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


List of Artifacts
~~~~~~~~~~~~~~~~~
* CentOS-7 RPMS
    * `dcache-5.1.0-1.xdc.noarch.rpm <http://repo.indigo-datacloud.eu/repository/xdc/production/1/centos7/x86_64/base/repoview/dcache.html>`_
    * `dcache-srmclient-5.1.0-1.xdc.noarch.rpm <http://repo.indigo-datacloud.eu/repository/xdc/production/1/centos7/x86_64/base/repoview/dcache-srmclient.html>`_


* Ubuntu 16.04 DEBS
    * 