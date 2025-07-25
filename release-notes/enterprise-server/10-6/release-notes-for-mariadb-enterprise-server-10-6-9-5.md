# Release Notes for MariaDB Enterprise Server 10.6.9-5

MariaDB Enterprise Server 10.6.9-5 is a maintenance release of [MariaDB Enterprise Server](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/mariadb-enterprise-server/README.md) 10.6. This release includes a variety of fixes.

MariaDB Enterprise Server 10.6.9-5 was released on 2022-09-12.

## Fixed Security Vulnerabilities

| CVE (with [cve.org](https://github.com/mariadb-corporation/docs-release-notes/blob/test/mariadb-enterprise-server-release-notes/mariadb-enterprise-server-10-6/cve.org) link) | CVSS base score |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| [CVE-2023-5157](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-5157)                                                                                                 | 7.5             |
| [CVE-2018-25032](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-25032)                                                                                               | 7.5             |
| [CVE-2022-32091](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32091)                                                                                               | 6.5             |
| [CVE-2022-32089](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32089)                                                                                               | 6.5             |
| [CVE-2022-32084](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32084)                                                                                               | 6.5             |
| [CVE-2022-32082](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32082)                                                                                               | 6.5             |
| [CVE-2022-32081](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-32081)                                                                                               | 6.5             |

## Backported Features

MariaDB Enterprise Server enables a predictable development and operations experience through an [enterprise lifecycle](../enterprise-server-lifecycle.md). These new features have been backported after reaching maturity in MariaDB Community Server:

* The `UUID` data type has been backported from MariaDB Community Server 10.7 for more efficient storage of `UUID` values. (MENT-1459)

## Notable Changes

* Galera has been updated to `26.4.13-1`
* Debian 9 support has been discontinued.
* Red Hat Enterprise Linux 9 support has been added.
* Rocky Linux 9 support has been added.
* The [--max-statement-time](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump#options) command-line option has been added for [mariadb-dump](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump) with a default value of 0. ([MDEV-18702](https://jira.mariadb.org/browse/MDEV-18702))
* Session scope has been added for the [explicit\_defaults\_for\_timestamp system variable](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#explicit_defaults_for_timestamp), in addition to global scope. ([MDEV-29225](https://jira.mariadb.org/browse/MDEV-29225))
* OpenSSL 3.0 support has been added for MariaDB Enterprise Cluster (powered by Galera) ([MDEV-25949](https://jira.mariadb.org/browse/MDEV-25949))

## Issues Fixed

### Can result in data loss

* When [mariadb-backup](broken-reference) is executed with the `--rsync` command-line option, the backup tries to copy the InnoDB buffer pool dump file, which is located at the path defined by the [innodb\_buffer\_pool\_filename system variable](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_buffer_pool_filename). ([MDEV-28781](https://jira.mariadb.org/browse/MDEV-28781))
  * Starting with this release, [mariadb-backup](broken-reference) only copies the InnoDB buffer pool dump file during State Snapshot Transfers (SSTs) for MariaDB Enterprise Cluster, powered by Galera.
* With MariaDB Enterprise Cluster, when [read\_only](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#read_only) is enabled on a node, users without the [SUPER privilege](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/account-management-sql-statements/grant#super) can still write to the node. ([MDEV-28546](https://jira.mariadb.org/browse/MDEV-28546))
* With MariaDB Enterprise Cluster, when a value is retrieved from an InnoDB sequence using the [NEXTVAL() function](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-structure/sequences/sequence-functions/nextval), the change is not replicated. ([MDEV-27862](https://jira.mariadb.org/browse/MDEV-27862))
  * Starting with this release, InnoDB sequences are properly replicated when they are defined with `NOCACHE`.
* When an InnoDB table's collation is changed using [ALTER TABLE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/alter/alter-table) with the `INPLACE` or `NOCOPY` algorithms, duplicate entries in unique indexes are not detected. ([MDEV-26294](https://jira.mariadb.org/browse/MDEV-26294))
* When InnoDB performs crash recovery on startup, recovery can fail when the redo log contains DDL statements. ([MDEV-28864](https://jira.mariadb.org/browse/MDEV-28864), [MDEV-28870](https://jira.mariadb.org/browse/MDEV-28870), [MDEV-28923](https://jira.mariadb.org/browse/MDEV-28923), [MDEV-28977](https://jira.mariadb.org/browse/MDEV-28977))

### Can result in a hang or crash

* When `INSERT .. SELECT .. GROUP BY` is executed and the `GROUP BY` clause contains a derived table, the server can crash. ([MDEV-28617](https://jira.mariadb.org/browse/MDEV-28617))
* When a query contains an `ANY(SELECT .. GROUP BY(SELECT ..))` predicand with a redundant subquery in the `GROUP BY` clause, the server can crash. ([MDEV-29139](https://jira.mariadb.org/browse/MDEV-29139))
* When [ALTER TABLE .. ADD](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/alter/alter-table) is used to add a column with the `INSTANT` algorithm, the server can crash if the `ROW_FORMAT` in the `.frm` file does not match the actual row format used by the data file. ([MDEV-26577](https://jira.mariadb.org/browse/MDEV-26577))
  * For tables created prior to MariaDB Server 10.2, the `ROW_FORMAT` in the `.frm` file could be inconsistent with the actual row format used by the data file. If the server were upgraded to MariaDB Enterprise Server 10.6, the inconsistency could remain.
* When `INSERT .. SELECT` is executed and the `SELECT` query calls an aggregate or window function, the server can crash with a segmentation fault. ([MDEV-26427](https://jira.mariadb.org/browse/MDEV-26427))
* When the [JSON\_EXTRACT() function](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_extract) is called, the server can crash with a segmentation fault. ([MDEV-29188](https://jira.mariadb.org/browse/MDEV-29188))
* When a query uses the `DISTINCT` keyword and calls an aggregate function as an argument for an always-constant function, the server can crash. ([MDEV-23809](https://jira.mariadb.org/browse/MDEV-23809))
  * An always-constant function is a function that always returns a constant value, even if the function's arguments are not constant.
  * For example, the [COLLATION() function](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/secondary-functions/information-functions/collation) is an always-constant function.
* When [mariadb-backup](broken-reference) is executed with the [--compress](broken-reference) and [--parallel](broken-reference) options, the backup can hang due to a race condition between threads. ([MDEV-29043](https://jira.mariadb.org/browse/MDEV-29043))
* When an `EXISTS` predicate or an `IN`, `ALL`, or `ANY` predicand is used in an eliminated GROUP BY clause, the server can crash. (MENT-1606, [MDEV-29350](https://jira.mariadb.org/browse/MDEV-29350))
* When an `IN` subquery is used outside the context of a regular query (such as in a stored procedure), the server can crash. ([MDEV-22001](https://jira.mariadb.org/browse/MDEV-22001))
* When MariaDB Enterprise Cluster is used and the Galera replication TCP port receives non-Galera network traffic, the server can crash. ([MDEV-25068](https://jira.mariadb.org/browse/MDEV-25068))
  * In previous releases, when the crash occurred, the following messages would appear in the [MariaDB error log](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/server-monitoring-logs/error-log):

```
terminate called after throwing an instance of 'boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<std::system_error> >'
what(): remote_endpoint: Transport endpoint is not connected
[ERROR] mysqld got signal 6 ;
```

* When a generated column is added to an InnoDB table with the INSTANT algorithm, the server can crash due to a buffer overflow. ([MDEV-26420](https://jira.mariadb.org/browse/MDEV-26420))
* When [CREATE VIEW](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/views/create-view) is executed with a view definition that contains an unknown column in an ON condition, the server can crash instead of raising an error with the [ER\_BAD\_FIELD\_ERROR error code](https://github.com/mariadb-corporation/docs-server/blob/test/release-notes/enterprise-server/10-6/broken-reference/README.md). ([MDEV-29088](https://jira.mariadb.org/browse/MDEV-29088))
* When [FLUSH BINARY LOGS](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/server-monitoring-logs/binary-log) is executed, the server can hang. ([MDEV-28948](https://jira.mariadb.org/browse/MDEV-28948))
* When the [innodb\_open\_files system variable](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/innodb/innodb-system-variables#innodb_open_files) is too low, the server can crash if InnoDB accesses too many tables or partitions. ([MDEV-26293](https://jira.mariadb.org/browse/MDEV-26293))
* When InnoDB detects a corrupt data page, the server can crash. ([MDEV-22388](https://jira.mariadb.org/browse/MDEV-22388), [MDEV-21098](https://jira.mariadb.org/browse/MDEV-21098), [MDEV-13542](https://jira.mariadb.org/browse/MDEV-13542), [MDEV-28457](https://jira.mariadb.org/browse/MDEV-28457), [MDEV-18519](https://jira.mariadb.org/browse/MDEV-18519), [MDEV-22388](https://jira.mariadb.org/browse/MDEV-22388))
* When InnoDB performs crash recovery on startup, the server can crash when the redo log contains a [RENAME TABLE statement](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/rename-table) performed against a table located in the system tablespace. ([MDEV-28752](https://jira.mariadb.org/browse/MDEV-28752))

### Can result in unexpected behavior

* For multi-table [UPDATE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/changing-deleting-data/update) or [DELETE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/changing-deleting-data/delete) queries, the optimizer fails to apply partition pruning optimization for the table that is updated or deleted from. ([MDEV-28246](https://jira.mariadb.org/browse/MDEV-28246))
* When an `IN` condition contains a mixture of numeric and string values, results can be inconsistent. ([MDEV-21445](https://jira.mariadb.org/browse/MDEV-21445))
* When a sequence event is written to the binary log with [binlog\_format=ROW](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables#binlog_format), the value of [binlog\_row\_image](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables) is not respected. ([MDEV-28487](https://jira.mariadb.org/browse/MDEV-28487))
* When a transaction can't be fully written to the binary log, but the transaction can be safely rolled back, a `LOST_EVENTS` incident event is written to the binary log. ([MDEV-21443](https://jira.mariadb.org/browse/MDEV-21443))
  * In previous releases, this problem could cause replica servers to encounter the following error:

```
Last_SQL_Errno	1590
Last_SQL_Error	The incident LOST_EVENTS occurred on the master. Message: error writing to the binary log
```

* Starting with this release, a `LOST_EVENTS` incident is only written to the binary log when safe rollback is not possible.
* When a replica server replicates an incident event, the details about the failure are not in the primary server's error log, the replica server's error log, or the output of [SHOW REPLICA STATUS](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/administrative-sql-statements/show/show-replica-status). ([MDEV-21087](https://jira.mariadb.org/browse/MDEV-21087))
* When a backup is performed with [mariadb-backup](broken-reference), the backup includes binary logs. ([MDEV-28758](https://jira.mariadb.org/browse/MDEV-28758))
* When a table is created from a [SELECT statement](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/selecting-data/select) that uses a recursive CTE, the table can use unexpected data types and contain truncated data if the calculated values from the recursive part of the CTE do not fit in the column types that are taken from the non-recursive part of the CTE. ([MDEV-12325](https://jira.mariadb.org/browse/MDEV-12325))
  * Starting with this release, the CTE calculation is aborted when the calculated values do not fit in the column types. When this occurs, a warning or error (depending on `sql_mode` is raised with the [ER\_WARN\_DATA\_OUT\_OF\_RANGE error code](https://github.com/mariadb-corporation/docs-server/blob/test/release-notes/enterprise-server/10-6/broken-reference/README.md) and the following error message:

```
Out of range value for column 'COLUMN_NAME' at row ROW_NUM
```

* When [mariadb client](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/mariadb/README.md) uses `EditLine` instead of `readline` (such as on Debian and Ubuntu), Unicode characters are not accepted. ([MDEV-28197](https://jira.mariadb.org/browse/MDEV-28197))
* When the optimizer chooses a semi-join optimization for a subquery, the LooseScan and FirstMatch strategies are not considered for certain queries where they would be appropriate, and they are considered for certain queries where they would be inappropriate. ([MDEV-28749](https://jira.mariadb.org/browse/MDEV-28749))
* When `FULLTEXT` search is performed on an InnoDB table, the results are incorrect when the search term contains an apostrophe ('). ([MDEV-20797](https://jira.mariadb.org/browse/MDEV-20797))
  * Starting with this release, when a search term contains an apostrophe ('), InnoDB tokenizes the word at the apostrophe, ignores the first token, and matches against the second token.
* After upgrading from old versions of MariaDB Server, some [ALTER TABLE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/alter/alter-table) operations fail if `ALGORITHM=NOCOPY` is specified. ([MDEV-28727](https://jira.mariadb.org/browse/MDEV-28727))
  * In previous releases, the following error could be raised:

```
ERROR 1845 (0A000): ALGORITHM=NOCOPY is not supported for this operation. Try ALGORITHM=INPLACE
```

* When [optimizer\_switch='not\_null\_range\_scan=on'](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#optimizer_switch) is set, queries that use table elimination can produce incorrect results. ([MDEV-28858](https://jira.mariadb.org/browse/MDEV-28858))
  * Table elimination is used when the query performs a JOIN and has `const` tables.
* When a replica server is replicating from a primary server that is too old to write [explicit\_defaults\_for\_timestamp](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#explicit_defaults_for_timestamp) to the binary log, the replica server ignores its own value and assumes that the value should be `OFF`. ([MDEV-29078](https://jira.mariadb.org/browse/MDEV-29078))
  * Starting with this release, the replica server determines an optimal value for [explicit\_defaults\_for\_timestamp](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#explicit_defaults_for_timestamp) based on the version of the primary server. If the primary server is too old to write its value to the binary log, the replica server uses its own value.
* When a `UUID` or `INET6` column is referenced in a `WHERE col IN(SELECT ..)` subquery of an [UPDATE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/changing-deleting-data/update) or [DELETE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/changing-deleting-data/delete) statement, the query does not affect the correct number of rows. ([MDEV-28491](https://jira.mariadb.org/browse/MDEV-28491))
* When a [BINARY](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/data-types/string-data-types/binary) column is used to store `UUID`s and a [SELECT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/selecting-data/select) statement filters the column with an `IN` clause, the query can be very slow if the `UUID`s are specified in hexadecimal. ([MDEV-25020](https://jira.mariadb.org/browse/MDEV-25020))
* [DROP DATABASE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/drop/drop-database) is case-insensitive. ([MDEV-28802](https://jira.mariadb.org/browse/MDEV-28802))
* When [mariadb-backup](broken-reference) is used to prepare a backup, the operation can fail if the backup contains DDL. ([MDEV-28974](https://jira.mariadb.org/browse/MDEV-28974))
  * In previous releases, when the backup failed, the output could contain messages like the following:

```
[ERROR] InnoDB: Attempted to open a previously opened tablespace. Previous tablespace:./DATABASE_NAME/TABLE_NAME.ibd uses space ID: SPACE_ID. Cannot open filepath: DATABASE_NAME/TABLE_NAME.ibd which uses the same space ID.
[Warning] InnoDB: We do not continue the crash recovery, because the table may become corrupt if we cannot apply the log records in the InnoDB log to it. To fix the problem and start mariadbd:
[Note] InnoDB: 1) If there is a permission problem in the file and mysqld cannot open the file, you should modify the permissions.
[Note] InnoDB: 2) If the tablespace is not needed, or you can restore an older version from a backup, then you can remove the .ibd file, and use --innodb_force_recovery=1 to force startup without this file.
[Note] InnoDB: 3) If the file system or the disk is broken, and you cannot remove the .ibd file, you can set --innodb_force_recovery.
##mariadb-backup##: srv_start() returned 11 (Generic error).
```

* When [mariadb-backup](broken-reference) is used to perform a backup while DDL is being executed, the output can contain excessive messages about DDL tracking. ([MDEV-29137](https://jira.mariadb.org/browse/MDEV-29137))
  * In previous releases, the output could contain many messages like the following:

```
DDL tracking : modify SPACE_ID "./DATABASE_NAME/TABLE_NAME.ibd"
```

* When the [JSON\_ARRAY,](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_array) [JSON\_ARRAY\_APPEND,](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_array_append) [JSON\_ARRAY\_INSERT,](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_array_insert) [JSON\_INSERT,](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_insert) [JSON\_SET,](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_set) or [JSON\_REPLACE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-functions/special-functions/json-functions/json_replace) functions are called with a [LONGTEXT](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/data-types/string-data-types/longtext) column, the result is truncated. ([MDEV-29264](https://jira.mariadb.org/browse/MDEV-29264))

## Changes in Storage Engines

* This release originally incorporated [MariaDB ColumnStore storage engine version 22.08.1](../../columnstore/columnstore-22-08/mariadb-columnstore-22-08-1-release-notes.md).
* This release previously incorporated [MariaDB ColumnStore storage engine version 22.08.2](../../columnstore/columnstore-22-08/mariadb-columnstore-22-08-2-release-notes.md).
* This release previously incorporated [MariaDB ColumnStore storage engine version 22.08.3](../../columnstore/columnstore-22-08/mariadb-columnstore-22-08-3-release-notes.md).
* This release now incorporates [MariaDB ColumnStore storage engine version 22.08.4](../../columnstore/columnstore-22-08/mariadb-columnstore-22-08-4-release-notes.md).

## Interface Changes

* [columnstore\_cmapi\_host](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable added
* [columnstore\_cmapi\_key](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable added
* [columnstore\_cmapi\_port](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable added
* [columnstore\_cmapi\_version](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable added
* [columnstore\_s3\_key](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable added
* [columnstore\_s3\_region](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable added
* [columnstore\_s3\_secret](https://app.gitbook.com/s/rBEU9juWLfTDcdwF3Q14/management/columnstore-system-variables) system variable added
* [explicit\_defaults\_for\_timestamp](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#explicit_defaults_for_timestamp) system variable dynamic changed from `No` to `Yes`
* `mariadb` --enable-cleartext-plugin command-line option added
* `mariadb-backup` --sst-max-binlogs command-line option removed
* `mariadb-dump` [--max-statement-time](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump#options) command-line option added
* `mariadbd` --spider-direct-aggregate command-line option added
* [spider\_direct\_aggregate](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/spider-status-variables) system variable added
* `sys_guid` FUNCTION plugin added
* `uuid` DATA TYPE plugin added
* `uuid` FUNCTION plugin added

## Platforms

In alignment to the [enterprise lifecycle](https://app.gitbook.com/o/diTpXxF5WsbHqTReoBsS/s/aEnK0ZXmUbJzqQrTjFyb/~/changes/32/mariadb-enterprise-server-release-notes/enterprise-server-lifecycle), MariaDB Enterprise Server 10.6.9-5 is provided for:

* CentOS 7 (x86\_64)
* Debian 10 (x86\_64, ARM64)
* Debian 11 (x86\_64, ARM64)
* Microsoft Windows (x86\_64)
* Red Hat Enterprise Linux 7 (x86\_64)
* Red Hat Enterprise Linux 8 (x86\_64, ARM64)
* Red Hat Enterprise Linux 9 (x86\_64, ARM64)
* Rocky Linux 8 (x86\_64, ARM64)
* Rocky Linux 9 (x86\_64, ARM64)
* SUSE Linux Enterprise Server 12 (x86\_64)
* SUSE Linux Enterprise Server 15 (x86\_64, ARM64)
* Ubuntu 18.04 (x86\_64, ARM64)
* Ubuntu 20.04 (x86\_64, ARM64)
* Ubuntu 22.04 (x86\_64, ARM64)

Some components of MariaDB Enterprise Server might not support all platforms. For additional information, see [MariaDB Corporation Engineering Policies".](https://mariadb.com/engineering-policies)

### Installation Instructions

* [MariaDB Enterprise Server ](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.6](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)
* [Enterprise Cluster Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Primary/Replica Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [ColumnStore Object Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)
* [ColumnStore Shared Local Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)
* [HTAP Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and Object Storage](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Sharded Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/sharded-mariadb-enterprise-spider-topology)[10](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[.](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/sharded-mariadb-enterprise-spider-topology)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Federated Topology with MariaDB Enterprise Server 10.](https://app.gitbook.com/s/0pSbu5DcMSW4KwAkUcmX/maxscale-architecture/mariadb-enterprise-spider-topologies/federated-mariadb-enterprise-spider-topology)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)

## Upgrade Instructions

* [Upgrade to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-from-to-specific-versions/upgrading-from-mariadb-10-5-to-mariadb-10-6)
* [Upgrade from MariaDB Community Server to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-between-major-mariadb-versions)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
