# Connector/J 1.5.0 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.org/connector-java/1.5.0/)[Release Notes](mariadb-connector-j-150-release-notes.md)[Changelog](../changelogs/1.5/mariadb-connector-j-150-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 1 Aug 2016

MariaDB Connector/J 1.5.0 is a [_**Release candidate**_](../../../community-server/about/release-criteria.md) _**(RC)**_\
release.

**For a description of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Notable Changes

This version is a feature release.

### Use native SSPI windows implementation

[CONJ-295](https://jira.mariadb.org/browse/CONJ-295).

kerberos implementation on windows has java limitations. Main limitations are :

* need a windows registry entry (HKEY\_LOCAL\_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters\AllowTGTSessionKey) so windows shared current ticket to java.
* java kinit must be executed to create a Ticket.
* restriction when client with local admin rights

See [see openJDK issue](https://bugs.openjdk.java.net/browse/JDK-6722928) for more informations

Kerberos GSSAPI implementation on windows in now based on [Waffle](https://github.com/dblock/waffle) that support windows SSPI based on [JNA](https://github.com/java-native-access/jna).\
If waffle-jna (and dependencies) is on classpath, native implementation will automatically be used.

This removes all those limitations.

### Support for TLSv1.1 and TLSv1.2

[CONJ-249](https://jira.mariadb.org/browse/CONJ-249)/[CONJ-301](https://jira.mariadb.org/browse/CONJ-301)

Driver before version 1.5 support only TLSv1.\
Default supported protocol are now TLSv1 and TLSv1.1, other protocols can be activated by options.

MariaDB and MySQL community server permit TLSv1 and TLSv1.1.\
MariaDB server from version 10.0.15 is using the openSSL library permitting TLSv1.2 (>= 5.5.41 for the 5.5 branch)._YaSSL doesn't support TLSv1.2, so if MariaDB server is build from sources with YaSSL, only TLSv1 and TLSv1.1 will be available, even for version > 10.0.15_

TLSv1.2 can be enabled by setting option `enabledSslProtocolSuites` to values `"TLSv1, TLSv1.1, TLSv1.2"`.

A new option `enabledSslCipherSuites` permit to set specific cipher.

New Options :

| enabledSslProtocolSuites | enabledSslCipherSuites                                                                                                                                                               |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| enabledSslProtocolSuites | Force TLS/SSL protocol to a specific set of TLS versions (comma separated list). Example : "TLSv1, TLSv1.1, TLSv1.2"Default: TLSv1, TLSv1.1. Since 1.5.0                             |
| enabledSslCipherSuites   | Force TLS/SSL cipher (comma separated list). Example : "TLS\_DHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384, TLS\_DHE\_DSS\_WITH\_AES\_256\_GCM\_SHA384"Default: use JRE ciphers. Since 1.5.0 |

### Performance improvement

[CONJ-291](https://jira.mariadb.org/browse/CONJ-291)

Different performance improvement have been done :

* Using PreparedStatement on client side use a simple query parser to identify query parameters. This parsing was taking up to 7% of query time, reduced to 3%.
* Better UTF-8 decoding avoiding memory consumption and gain 1-2% query time for big String.
* client parsing optimization : rewriteBatchedStatements (insert into ab (i) values (1) and insert into ab (i) values (2) rewritten as insert into ab (i) values (1), (2))\
  is now 19% faster (Depending on queries 40-50% of CPU time was spend testing that buffer size is big enough to contain query).
* there was some memory wastage when query return big resultset (> 10kb), slowing query.
* and a lot more

[CONJ-320](https://jira.mariadb.org/browse/CONJ-320)\
Batch improvement :\
Send X command without reading results, and read those X results asynchronously .\
Basically that permit to avoid a lot of 'ping-pong' between driver and server.

New Options :

| useBatchMultiSend       | useBatchMultiSendNumber                                                                                        |
| ----------------------- | -------------------------------------------------------------------------------------------------------------- |
| useBatchMultiSend       | PreparedStatement.executeBatch() will send many QUERY before reading result packets.Default: true. Since 1.5.0 |
| useBatchMultiSendNumber | When using useBatchMultiSend, indicate maximum query that can be send at a time.Default: 100. Since 1.5.0      |

### Prepare + execute in one call

[CONJ-296](https://jira.mariadb.org/browse/CONJ-296)

When using MySQL/MariaDB prepared statement, there will be 3 exchanges with server :

* PREPARE - Prepares statement for execution.
* EXECUTE - Executes a prepared statement preparing by a PREPARE statement.
* DEALLOCATE PREPARE - Releases a prepared statement.

See [Server prepare documentation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/prepared-statements/prepare-statement) for more information.

Since [MariaDB 10.2.2](../../../community-server/old-releases/release-notes-mariadb-10-2-series/mariadb-1022-release-notes.md), last PREPARE statement id can be identified with value "-1".\
Driver is using this functionality to PREPARE and EXECUTE in one client-server round-trip.

### Client logging

Client logging can be enable, permitting to log query information, execution time and different failover informations.\
This implementation need the standard SLF4J dependency.

New Options :

| log                     | maxQuerySizeToLog                                                                                                                                                                                                | slowQueryThresholdNanos | profileSql |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ---------- |
| log                     | Enable log information. require Slf4j version > 1.4 dependency.Default: false. Since 1.5.0                                                                                                                       |                         |            |
| maxQuerySizeToLog       | Only the first characters corresponding to this options size will be displayed in logsDefault: 1024. Since 1.5.0                                                                                                 |                         |            |
| slowQueryThresholdNanos | Will log query with execution time superior to this value (if defined )Default: 1024. Since 1.5.0                                                                                                                |                         |            |
| profileSql              | log connection id, query and execution time.log example : 2016-07-29 23:28:50 \[main] INFO org.mariadb.jdbc.MariaDbStatement - Query - conn:10295 - 0,309 ms - "select \* from TABLE"Default: false. Since 1.5.0 |                         |            |

### "LOAD DATA INFILE" Interceptors

[CONJ-305](https://jira.mariadb.org/browse/CONJ-305)\
LOAD DATA INFILE The fastest way to load many datas is using query [LOAD DATA INFILE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/inserting-loading-data/load-data-into-tables-or-index/load-data-infile).\
Problem is using "LOAD DATA LOCAL INFILE" (ie : loading a file from client), may be a security problem :

* A "man in the middle" proxy server can change the actual file asked from server so client will send a Local file to this proxy.
* If someone has can execute query from client, he can have access to any file on client (according to the rights of the user running the client process).

See [load-data-infile documentation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/inserting-loading-data/load-data-into-tables-or-index/load-data-infile) for more information.

Interceptors can now filter LOAD DATA LOCAL INFILE query's file location to validate path / file name.\
Those interceptors:

* Must implement interface `org.mariadb.jdbc.LocalInfileInterceptor`.
* Use [ServiceLoader](https://docs.oracle.com/javase/7/docs/api/java/util/ServiceLoader.html) implementation, so interceptors classes must be listed in file META-INF/services/org.mariadb.jdbc.LocalInfileInterceptor.

Example:

```java
package org.project;
public class LocalInfileInterceptorImpl implements LocalInfileInterceptor {
    @Override
    public boolean validate(String fileName) {
        File file = new File(fileName);
        String absolutePath = file.getAbsolutePath();
        String filePath = absolutePath.substring(0,absolutePath.lastIndexOf(File.separator));
        return filePath.equals("/var/tmp/exchanges");
    }
}
```

file META-INF/services/org.mariadb.jdbc.LocalInfileInterceptor must exist with content `org.project.LocalInfileInterceptorImpl`.

You can get ride of defining the META-INF/services file using [google auto-service](https://github.com/google/auto/tree/master/service) framework, permitting to use annotation `@AutoService(LocalInfileInterceptor.class)` that will register the implementation as a service automatically.

Using the previous example:

```java
@AutoService(LocalInfileInterceptor.class)
public class LocalInfileInterceptorImpl implements LocalInfileInterceptor {
    @Override
    public boolean validate(String fileName) {
        File file = new File(fileName);
        String absolutePath = file.getAbsolutePath();
        String filePath = absolutePath.substring(0,absolutePath.lastIndexOf(File.separator));
        return filePath.equals("/var/tmp/exchanges");
    }
}
```

### Minor evolution

* [CONJ-260](https://jira.mariadb.org/browse/CONJ-260) : Add jdbc nString, nCharacterStream, nClob implementation

### Bugfix

* [CONJ-316](https://jira.mariadb.org/browse/CONJ-316) : Wrong Exception thrown for ScrollType TYPE\_SCROLL\_INSENSITIVE
* [CONJ-298](https://jira.mariadb.org/browse/CONJ-298) : Error on Callable function exception when no parameter and space before parenthesis
* [CONJ-314](https://jira.mariadb.org/browse/CONJ-314) : Permit using Call with Statement / Prepare Statement

## Changelog

For a list of all changes made in this release, with links to detailed\
information on each push, see the[changelog](../changelogs/1.5/mariadb-connector-j-150-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
