# MaxScale 1.4 Changelog

* Authentication now allows table level resolution of grants. MaxScale service\
  users will now need SELECT privileges on `mysql.tables_priv` to be able to\
  authenticate users at the database and table level.
* Firewall filter allows whitelisting.
* Client side SSL works.

For more details, please refer to[_MaxScale 1.4.5 Release Notes_](maxscale-14-release-notes/mariadb-maxscale-145-release-notes-2017-02-01.md) [MaxScale 1.4.4 Release Notes](maxscale-14-release-notes/mariadb-maxscale-144-release-notes.md)[_MaxScale 1.4.3 Release Notes_](maxscale-14-release-notes/mariadb-maxscale-143-release-notes.md) [MaxScale 1.4.2 Release Notes](maxscale-14-release-notes/mariadb-maxscale-142-release-notes.md)[_MaxScale 1.4.1 Release Notes_](maxscale-14-release-notes/mariadb-maxscale-141-release-notes.md) [MaxScale 1.4.0 Release Notes](maxscale-14-release-notes/mariadb-maxscale-140-beta-release-notes.md).

### MaxScale 1.3

* Added support for persistent backend connections
* The binlog server is now an integral component of MaxScale.
* The logging has been changed; instead of different log files there is one log file and different message priorities.

For more details, please refer to [MaxScale 1.3 Release Notes](maxscale-14-release-notes/mariadb-maxscale-13-release-notes.md)

### MaxScale 1.2

* Logfiles have been renamed. The log names are now named error.log, messages.log, trace.log and debug.log.

### MaxScale 1.1.1

* Schemarouter now also allows for an upper limit to session commands.
* Schemarouter correctly handles SHOW DATABASES responses that span multiple buffers.
* Readwritesplit and Schemarouter now allow disabling of the session command history.

### MaxScale 1.1

**NOTE:** MaxScale default installation directory has changed to `/usr/local/mariadb-maxscale` and the default password for MaxAdmin is now ´mariadb´.

* New modules added
  * Binlog router
  * Firewall filter
  * Multi-Master monitor
  * RabbitMQ logging filter
  * Schema Sharding router
* Added option to use high precision timestamps in logging.
* Readwritesplit router now returns the master server's response.
* New readwritesplit router option added. It is now possible to control the amount of memory readwritesplit sessions will consume by limiting the amount of session modifying statements they can execute.
* Minimum required CMake version is now 2.8.12 for package building.
* Session idle timeout added for services. More details can be found in the configuration guide.
* Monitor API is updated to 2.0.0. Monitors with earlier versions of the API no longer work with this version of MaxScale.
* MaxScale now requires libcurl and libcurl development headers.
* Nagios plugins added.
* Notification service added.
* Readconnrouter has a new "running" router\_option. This allows it to use any running server as a valid backend server.
* Database names can be stripped of escape characters with the `strip_db_esc` service parameter.

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
