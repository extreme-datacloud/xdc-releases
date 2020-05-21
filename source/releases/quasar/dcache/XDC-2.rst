vXDC-2
------------

What’s new
~~~~~~~~~~

Upstream corresponding version: v. 6.1.3

**Highlights**

- dCacheView: uses inotify-over-SSE to keep page up-to-date.
- storage-events: added missing events in inotify-over-SSE.
- storage-events: performance and robustness improvements for inotify-over-SSE 
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

- **Alarms**

  - eliminate logback context from junit test (6f5242f268)
  - sending alarms events in json format (5b5d951096)
  - move to logback 1.1.4 and fix handling of MDC (5733f5e60c)
  - add pool dead alarm (7cc4963ad6)
  - wrap billing data source with AlarmEnabledDataSource (f29ddeab04)

- **billing**:

  - add capability for automatic truncation of fine-grained info tables (be520165b4)

- **chimera-shell**:

  - fix class cast of extractor in constructor (aaecade7e4)
  - should show output when commands come from stdin. (ad30a1d526)

* **DCAP**

  * use CacheEntryInfoMessage instead of PoolCheckFileMessage (477c2bb681)
  * gsi bad client excessive logging (8b3e2217d4)
  * restart pool selection on OUT-OF-DATE error (87ae552206)
  * remove control channel support for 'strict-size` (a8b2986096)
  * fix premature close of kafka sender (388e6d2b6a)
  * stage request for unknown location results in NPE (babd708540)

* **Frontend**

  * make ErrorResponseProvider return the more specific error message (2e41f65c88)
    qos migration policy engine should not raise JVM error when no tape pool found (85202496e8)
    allow pool enable/disable to use boolean JSON value (3448267444)
    remove unnecessary login requirement on restores and transfers (3185607893)
    events inotify avoid holding global lock when sending events (c38555246c)
    events inotify fix deadlock (5366aca496)
    disable fallback-to-anonymous by default (39d66a2fb0)
    disabling basic authn should not disable macaroons (bca2869abf)
    update default to reject macaroons on unencrypted channels (ea3cdd48cb)
    add switch to reject macaroons sent unencrypted (690d7f9145)
    move QoS logic out of frontend (ccd6c3a24f)
    avoid NPE when request has no media type (74e90ab74c)
    notify PnfsManager of QoS transitions (9c4338f951)
    fix NPE if limit is not specified (0005a2d59f)
    fix QoS pin semantics (f1ce0a429d)
    avoid double fetch of sweeper data from pools (274c3139c5)
    make geographic placement configurable (6abfd149cf)
    include doors resource as request-scope bean (21fc553450)
    add HTTP entities in the access log file. (2377c86beb)
    add basic access logging (650063856b)
    include CDC in scheduled activity (21b1650492)
    fix race on client reconnecting (b91240daff)
    ensure client is disconnected when shutting down channel (ed41f74110)
    avoid race on cancelling channel garbage-collect task (82adce7015)
    undefined suid parameter on transfers should be NULL not "null" (8a7ced4cc5)

* **FTP**

  * avoid NullPointerException when client transfers without ALLO (8e11da115e)
    support zero allo values (527e8d35e0)
    avoid NPE on HA-Proxy probes (5e1b8490c7)
    enable aborted transfer logging by default (b03d514de4)
    add support for (explicit) FTPS doors (fb97274611)
    add support for anonymous FTP access (5cafe39aad)
    store calculated checksum using root privileges (186a407d7f)
    fix MLSC command for non-small directories (99ddbf5050)

* **gplazma**

  - scitoken: do not use javax.activation.MimeType (f9226d3b19)
    scitoken add partial support for WLCG Common JWT Profile scopes (11d21f1aaa)
    scitoken refactor plugin (6a87a2bc48)
    scitoken add SciTokenPlugin unit test (753712a39a)
    scitoken fix remote reading of JSON with UTF-8 CharSet (6a8cc96ead)
    multimap support files with multiple primary gids (648b880cd6)
    x509 avoid NPE if certificate has no EKU (b46555d040)
    x509 only map IGTF AP LoAs to REFEDS if entity is natural person (370a51278e)
    scitoken add unit tests and fix SciTokenScope (2a31529a6c)
    x509 add support for CAs asserting version-specific LoA policies (2c0d03e1bd)
    x509 include DN when logging incompatible LoAs (656dfa7ab6)
    scitoken fix two issues with SciToken plugin (ac24bb005d)
    oidc add support EGI LoAs (d71349fb73)
    x509 add heuristics to identify PERSON certificates (2a2f90fff1)
    oidc add support for eduperson_assurance claims (e719169fc4)
    ldap remove obsolete scala based plugin (dd48978ec0)
    x509 add heuristics for entity defn principals (e836fe1751)
    x509 include LoA from CA's .info file (19a36cd078)
    x509 update documentation link (f7f4f75132)
    scitoken add support for multiple audience claims (98cc34eb97)
    fix SciToken fetching remote content (224ece37d0)
    stop using sun.security.rsa.RSAPublicKeyImpl (235c71d9ab)
    Add how to enable scitokens in gplazma.conf (49ae166fcf)
    ldap avoid thread leak by explicitly close NamingEnumeration (926287f8e4)
    jaas Logger name was changed (a5a9ce3d61)
    nis updated name of logger to fit java convention (37d7a43800)
    multimap LOG changed to LOGGER (b71030d33e)
    voms log auf LOGGER geändert (4197d08661)
    htpasswd unification of LOGGER variable (7e987f3e6d)
    argus changed logger variable name (2a64a5c51c)
    nis update readme with up to date date (5286a17c29)
    consider bearer token when deciding whether to log failures (1461b4c3f1)
    x509 add extra OIDs for Key-Usage (bf7e4ea5b5)
    oidc better handling if JWT is unknown or invalid (e3c4223424)
    scitoken add SciToken support (7e8993fa45)
    ban add ability to select based on uid and gid (f7ac12a41a)
    oidc cache user-info lookup result (cd826a7d25)
    oidc fix broken commit (424f968388)
    oidc optimise network usage (4a1da8a569)
    oidc add discovery cache configuration properties (4c124a11d7)
    oidc warn slow user-info queries (2abff00b2e)
    oidc introspect JWT to learn issuer (ac5419d132)
    gridmap compare DNs ignoring letter case for attribute names (a4acb0ec79)
    jaas logs a stack-trace on misconfiguration (a95763ecce)
    voms add trust anchor refresh paramater (b7d3b663ac)
    x509 add support for REFEDS LoAs (08c05ea854)

- **httpd**:

  - escape status field in HttpPoolMgrEngineV3 (ec7babbaa5)
    allow file-specific errors to propagate (a1e0c1b46f)
    write requests on admin webpage to .access-log (01c9a760b1)
    http: fix usage info legend color and label (741e9896d3)

* **History**

  * guard against unconfigured sweeper histogram (beedd99fa7)
    protect against missing highest bin in histogram data (e8a77056c2)
    do not allow null composed json objects (3df1cd4302)
    expose refresh and timeout through admin commands (5de55707a0)

* **Info**

  * fix array index out of bound exception for admin commands (8cef28d383)
    publish a domain's zone (9379199b77)

* **NFS**

  *     don't use stream to compute collection size (a48e5e082b)
    extend host filter of 'show clients' command to accept patterns (d02f314529)
    raise an alarm when client reports connection issues with a pool (de09a3a6af)
    rename NFSv41Door#ioMessages -> transfers (ab90a1251e)
    avoid NPE on error path (b255159a3a)
    re-try stale mover (23bec2d2c8)
    restore transfers debug context on client retry (c95f73b323)
    do not wait for mover to shutdown for reads (22d935c84f)
    fix layoutreturn operation handling regression (c8cf843d33)
    restart stale transfers (3c44c62293)
    support ability to set file checksum(s) via dot command (0fb511cf27)
    checksum types dot command (765e95fef4)
    fix permissions on the pin dot command. (2a7f502f6f)
    check whether pin operations were accepted (d5aa2f6409)
    avoid stack-traces and provide feedback on invalid pset/fset args (4a596cf4c8)
    use client IP address when pinning files (e89de9da2b)
    add dot command to list a file's pins (f67ef81eff)
    fix NPE on "show transfers" command (f27fc7abe6)
    merge AccessLogAware and ProxyIo operation factories (b652f53090)
    introduce workaround 'permission deny' on layout commit (112f784fdd)
    handle read and write transfers by different transfer classes (a1cb89ef4d)
    fail with NO-SPACE error when all pools are full (91d3cbd813)
    enforce charset encoding when processing dot files (3dc0af4cb8)
    include CDC in scheduled activity (f41b4a9d1b)
    fix missing CDC initialization (00d89b7244)
    do not filter device's IP addresses based on site locality (606c8236b7)

* **PNFS Manager**

  * better explain restriction-based permission problems (5ee32d54d2)
    silence delivery failures for FileAttributesTopic (48ea014813)
    network issues triggered a NPE (277f773dd0)
    fix regression when querying attributes of the root directory (77b0b33708)
    include link information in storageinfo (968926535c)
    do not emit IN_ATTRIB event on atime updates (e4e841630f)
    add file attribute notification when AL/RP changes (3dfed7e8b0)

* **Pool**

  *     flush controller fix wrong setter type for queue order (d293b1e39e)
    remove disk copy if restore from HSM failed (efe932bcae)
    log when a queue starts to queue movers and when this stops (49072610d5)
    Fix tape-reserved size calculation (eb1b81de61)
    add pool name to POOL_DEAD alarm (b1dfe06a79)
    enable aborted transfer logging by default (b03d514de4)
    make berkeleyDBMetaDataRepository default (31cbb8cb2b)
    encrypted p2p transfer modes (daabc90edc)
    refactor JTM to use ScheduledExecutorService (2015acc37e)
    improve messages when migration job is cancelled. (db1e28987d)
    update "rep ls -s" formatting (67a8a2673a)
    include pool name in health-check reports (b184d20f61)
    fix annotation in PoolMigrationCopyReplicaMessage (2365d1363e)
    clean up master/push fc8dd482d13b8d089cce68859cfbb038cc7d8d48 (9f6cd9fc72)
    encrypted p2p transfers (fc8dd482d1)
    fix the xrootd version number on pool transfer service (473972bf3a)
    clean code for HttpsTransferService (12b4066b79)
    add host excluded unit tests and refactor (6dae458b4a)
    restructure httpsprofile (d779f40ff6)
    refactor to be more DRY (8ea611d1aa)
    make flush queue configurable as FIFO or LIFO (0dd6c45c1d)
    allow margin option on sweeper when reclaiming space (665a774f56)
    Improve metadata check speed on pool re-start. (da929a09b6)
    don't pass checksum module to transfer services (c7cf6c05a2)
    remove artifacts from the  replica manager (21b0efa44d)
    remove reference to checksum module (2aeb71bb63)
    update billing log message to say whether cancelled mover was queued (98d3cc8704)

* **Pool Manager**

  * add affinity requirements to PoolManagerMessage (cbffb34095)
    make RendezvousPoolManagerHandler#backendFor private (2328947565)
    fix pool's canonicalHostName change detection (part2) (4aeef4a0ed)
    fix pool's canonicalHostName change detection (e90b647ce8)
    support selection filter for excluding pools on given hosts (3bcb15a5ae)
    scan for matching pools when dynamic group is created (92e2926ee3)
    drop tags map argument in  DynamicPGroup#addIfMatches (67511527da)
    include pool tags into SelectionPool record (59becc2d34)
    always allow removal of dynamic pool group (c6d60dd6a5)
    do not check stage/p2p reply message type (d73bddada1)
    remove unused interface ExtendedRunnable (7ebb537b72)
    don't fallback selection links by default (c1f7183f3c)
    introduce dynamic pool groups based on pool tags (949936a21e)
    update 'rc failed' command (478049fbd4)
    update some psu commands to be consistent (b0839feca7)
    add ability to disable anonymous staging (3f5d8f8255)
    psu remove dead code (b5e076fd68)
    make actual network hostname of pool available (34561e5ebc)

* **Resilience**

  * fix broke commit cc4f25a3c8 (dca3f17305)
    don't use old data API (cc4f25a3c8)
    allow handling of QoS transitions for resilient files (e6534d4de2)
    avoid NPE if pool removed from resilience poolgroup (e29da0b9b1)
    override Object::equals, complete equals contract (4188f0e04a)
    don't compare Integer objects by refference (053dd1fd0a)
    add command to detect files all of whose replicas are on a given set of pools (c557f28a29)
    fix remove count when replica is precious (1f7b9eb9ad)
    remove reference to PoolCheckMessage in unit test (907eec604a)
    account for waiting states (12d872d53e)

* **SRM / SRM Manager**

  * use host IP for comparison when determining if SURL is local (e73815c05e)
    minor refactor of setting scheduler (4adebccbb7)
    rename method that accepts a new Job (a848d5cea4)
    remove deadcode from JobStorage classes (c86bf9de1e)
    refactor Scheduler to make acceptJob clearer (48a9fb2cf1)
    avoid redundant saveJob call (ec2db90e2f)
    use guava-style to check SURL validity (d47b9ba579)
    remove dead code, restrict code access (653983a630)
    introduce Job state change notification, update Scheduler to use it (dbd3b95caf)
    propagate srmmanager id into requests (cec4de4e76)
    refactor Job state-change (f817fa85aa)
    allow client to control whether srmPrepareToGet can trigger staging (86e4e23a73)
    log number of SURLs in an SRM request. (43f6472b84)
    improve access logging of srmBringOnline requests. (e228d41807)
    Remove JVM memory limits (a231e873af)
    use CacheEntryInfoMessage instead of PoolCheckFileMessage (477c2bb681)
    do not log a stack-trace on expected Exception errors (0dc483bdcc)
    include TLS/SSL port in 'dcache ports' command (9c526832cf)

* **WebDAV**

  * add support for RFC3230 Want-Digest on COPY command (1e9353e8de)
    include DAV header in OPTIONS requests. (bff16d656c)
    set Access-Control-Allow-Credentials to true (20e47c97c4)
    disable fallback-to-anonymous by default (39d66a2fb0)
    fix CORS when all clients are allowed to connect (fbed8eca0c)
    avoid logging non-error as an error (3d06ecc283)
    add allow header to OPTION method request (3dca2b59a2)
    changed name of Logger (c312637eb1)
    fix cross origin resources sharing issue (385b77fac2)
    return 405 status code for PUT requests targeting collections (d27558bb89)
    include CDC in scheduled activity (c334ea1c58)
    allow transfers as user with role 'admin' (f77fd77e27)
    fix resource name for door root (69669e6e3f)
    fix path-to-caveat for macaroon minting endpoint (33d957a899)
    fix NPE when Kafka notified file deletion (6c33d339a2)
    disabling basic authn should not disable macaroons (bca2869abf)
    update default to reject macaroons on unencrypted channels (ea3cdd48cb)
    fail COPY early if file is currently being uploaded (9cb63c2142)
    add switch to reject macaroons sent unencrypted (690d7f9145)
    note about redirects to HTTPS (b65acf64af)
    401 for unauthenticated requests; message in status line (63b864039e)
    work-around Milton racy API for creating collections (a7bc5ef250)
    fix name of root (a42022b6c1)
    add Content-Type and fix status (4560d3f4ba)

* **XRootD**

  * change URL to use hostname on redirect to pool (d9529e464c)
    don't initialize delegation provider when there is no gsi module (3512cdc24e)
    make door use CachingLoginStrategy (7d78c80bcb)
    support authz handlers which need to access login strategies (15e0c5da3d)
    refit checksum handling after xrootd4j bug fix (6c686376e8)
    honor read paths when listing directories (9d3b029bb2)
    refine error handling (71dfffa81e)
    support the 'tried' CGI in door (261e786395)
    fix `kill mover` command (a8cd5884a3)
    replace constants for version number (ead00eba6e)
    update protocol version numbers (e3a4d13ce5)
    add checksum cgi handling to door query (6cf74388bc)
    check the session for credential on source open (6f2e53e1f3)
    respond to tpc query correctly* (03f18cbfca)
    compute VOMs CA refresh interval using unit (1cc35dfdfe)
    add ability to override default timeout for server response (TPC) (f853024421)
    fix delegation client lifecycle management (71723b8c39)
    add full proxy delegation to door (4f8b8ba486)
    add full proxy delegation to door (d4f481c36e)
    implement proxy delegation client (b02a110df8)
    use debug level instead of trace (ddf9009b52)
    implement support for security level and signed hashes (094f99fc01)
    fix access logging when door is configured with HAproxy (137d2ed565)
    remove mv request hack (d936ee8bf4)
    Allow ROOT read access by destination server when dCache is the source in a third-party transfer. (71367f26e0)
    support mapping clients with valid credentials to NOBODY (806e8bc3d1)

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
    * `dcache-5.0.0-1.xdc.noarch.rpm <https://repo.indigo-datacloud.eu/repository/xdc/production/1/centos7/x86_64/base/repoview/dcache.html>`_


* Ubuntu 16.04 DEBS
    * `dcache-5.0.0-1.xdc.noarch.rpm <https://repo.indigo-datacloud.eu/repository/xdc/production/1/ubuntu/dists/xenial/main/binary-amd64/dcache_5.0.0-1.xdc_all.deb>`_ 
