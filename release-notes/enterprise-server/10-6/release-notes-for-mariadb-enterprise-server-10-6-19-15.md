# Release Notes for MariaDB Enterprise Server 10.6.19-15

MariaDB Enterprise Server 10.6.19-15 is a maintenance release of [MariaDB Enterprise Server](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/mariadb-enterprise-server/README.md) 10.6.

MariaDB Enterprise Server 10.6.19-15 was released on 2024-09-09.

## Backports

* Starting with MariaDB Enterprise Server 10.6.19-15, the space occupied by freed pages within the InnoDB system tablespace can be reclaimed by adding an :autoshrink attribute to innodb\_data\_file\_path, like: (MENT-1304)

```
[mariadb]
...
innodb_data_file_path=ibdata1:12M;ibdata2:50M:autoextend:autoshrink
```

This allows the system tablespace to be truncated after the last allocated page within it, all the way to the specified minimum size (here: 12MiB).

In older release series InnoDB data files never shrink in size during normal operation. One could shrink .ibd files by rebuilding tables with OPTIMIZE TABLE, or the undo tablespace files by `SET GLOBAL innodb_undo_log_truncate=ON`

* The function CONV() , which converts a number between numeric base systems, now supports conversions up to base 62. This allows conversions to encodings to capital letters A-Z, lower case letters a-z, and numbers 0-9. The old limit was 36, not including lower case letters. (MENT-2031)

Example:

```sql
SELECT CONV(61,10,36);
```

```
+----------------+
| CONV(61,10,36) |
+----------------+
| 1P             |
+----------------+
SELECT CONV(61,10,62);
+----------------+
| CONV(61,10,62) |
+----------------+
| z              |
+----------------+
```

* The JSON functions JSON\_ARRAY\_INTERSECT, JSON\_OBJECT\_TO ARRAY, and JSON\_FILTER\_KEYS have been backported from later MariaDB Community Server Release Series to enhance the JSON function coverage in this MariaDB Enterprise Server release series. (MENT-1897)
* The new JSON function JSON\_ARRAY\_INTERSECT(, ) is used to find the intersection between two JSON arrays.

Example:

```sql
SET @array1= '[1,2,3]';
SET @array2= '[1,2,4]';
SELECT json_array_intersect(@array1, @array2) AS result;
```

```
+--------+
| result |
+--------+
| [1, 2] |
+--------+
```

```sql
SET @json1= '[[1,2,3],[4,5,6],[1,1,1]]';
SET @json2= '[[1,2,3],[4,5,6],[1,3,2]]';
SELECT json_array_intersect(@json1, @json2) AS result;
```

```
+------------------------+
| result                 |
+------------------------+
| [[1, 2, 3], [4, 5, 6]] |
+------------------------+
```

* The new JSON function JSON\_OBJECT\_TO\_ARRAY(\<json\_doc>) is used to convert all JSON objects found in a JSON document to JSON arrays where each item in the outer array represents a single key-value pair from the object.\
  Example:

```sql
SET @json1= '{ "a" : [1,2,3] , "b": {"key1": "val1", "key2": {"key3": "val3"}} }';
SELECT JSON_OBJECT_TO_ARRAY(@json1) AS result;
```

```
+-----------------------------------------------------------------------+
| result                                                                |
+-----------------------------------------------------------------------+
| [["a", [1, 2, 3]], ["b", {"key1": "val1", "key2": {"key3": "val3"}}]] |
+-----------------------------------------------------------------------+
```

Resulting arrays can be compared using JSON\_ARRAY\_INTERSECT():

```sql
SET @json1='{"a":[1,2,3],"b":{"key1":"val1","key2":{"key3":"val3"}}}';
SET @json2='{"a":[1,2,3]}';
SELECT JSON_OBJECT_TO_ARRAY(@json1) INTO @array1;
SELECT JSON_OBJECT_TO_ARRAY(@json2) INTO @array2;
SELECT JSON_ARRAY_INTERSECT(@array1,@array2) AS result;
```

```
+--------------------+
| result             |
+--------------------+
| [["a", [1, 2, 3]]] |
+--------------------+
```

* The new JSON function JSON\_OBJECT\_FILTER\_KEYS(\<json\_doc>,\<array\_keys>) returns key/value pairs from a JSON string for keys defined in \<array\_keys>.\
  Example:

```sql
SET @json1= '{ "a": 1, "b": 2, "c": 3}';
SELECT JSON_OBJECT_FILTER_KEYS (@json1, ' ["b", "c"] ') AS result;
```

```
+------------------+
| result           |
+------------------+
| {"b": 2, "c": 3} |
+------------------+
```

By using JSON\_ARRAY\_INTERSECT() and JSON\_KEY() as arguments for JSON\_OBJECT\_FILTER\_KEYS(), a comparison of two JSON strings is possible where only the same keys are compared, not the key/value pairs.\
Example (only show key/value pairs of json1 where the key exists in json2):

```sql
SET @json1= '{ "a": 1, "b": 2, "c": 3}';
SET @json2= '{"b" : 10, "c": 20, "d": 30}';
SELECT JSON_OBJECT_FILTER_KEYS (@json1, json_array_intersect(json_keys(@json1), json_keys(@json2))) AS result;
```

```
+------------------+
| result           |
+------------------+
| {"b": 2, "c": 3} |
+------------------+
```

* The new JSON function JSON\_KEY\_VALUE(\<json\_doc>,\<json\_path>) extracts key/value pairs from a JSON object. The JSON path parameter is used to only return key/value pairs for matching JSON objects. (MENT-1896)

Example:

```sql
SELECT JSON_KEY_VALUE('[[1, {"key1":"val1", "key2":"val2"}, 3], 2, 3]', '$[0][1]');
```

```
+-----------------------------------------------------------------------------+
| JSON_KEY_VALUE('[[1, {"key1":"val1", "key2":"val2"}, 3], 2, 3]', '$[0][1]') |
+-----------------------------------------------------------------------------+
| [{"key": "key1", "value": "val1"}, {"key": "key2", "value": "val2"}]        |
+-----------------------------------------------------------------------------+
```

The function JSON\_KEY\_VALUE() can be used as an argument to JSON\_TABLE(), which allows adding the key to a result set.\
Example:

```sql
SELECT jt.* FROM JSON_TABLE(
JSON_KEY_VALUE('[[1, {"key1":"val1", "key2":"val2"}, 3], 2, 3]', '$[0][1]'),'$[*]'
COLUMNS (
k VARCHAR(20) PATH '$.KEY',
v VARCHAR(20) PATH '$.value',
id FOR ORDINALITY )) AS jt;
```

```
+------+------+------+
| k    | v    | id   |
+------+------+------+
| key1 | val1 |    1 |
| key2 | val2 |    2 |
+------+------+------+
```

## Notable Changes

* It is now possible to unblock an account which reached the `--max-password-errors` limit by `ALTER USER <user> ACCOUNT UNLOCK` instead of executing a `FLUSH PRIVILEGES` command ([MDEV-34311](https://jira.mariadb.org/browse/MDEV-34311))
  * Before this change `ALTER USER <user> ACCOUNT UNLOCK` only unlocked accounts which have been locked explicitly via `ALTER USER <user> ACCOUNT LOCK`
  * `FLUSH PRIVILEGES` was the only way to reset account limit counters, like accounts blocked by reaching `--max-password-errors`. Using `FLUSH PRIVILEGES` causes a full reload of the ACL tables, which can cause heavy disk reads
* A new global variable `server_uid` can be used to identify a server instance. This Server ID is also logged in the error log file on startup ([MDEV-34311](https://jira.mariadb.org/browse/MDEV-34311))
* A new `optimizer_join_limit_pref_ratio` optimization had been added which allows to efficiently handle queries using `JOIN and ORDER BY ... LIMIT` construct. The new system variable `optimizer_join_limit_pref_ratio` is set to 0 by default for disabling the optimization. Set the value of `optimizer_join_limit_pref_ratio` to a non-zero value to enable this option (higher values are more conservative, recommended value is 100)
* Galera has been updated to `26.4.19`
  * The GCS protocol version has been changed, preventing a downgrade of individual nodes of a MariaDB Enterprise Cluster

## Changes in Storage Engines

* This release incorporates MariaDB ColumnStore engine version 23.10.2.

## Issues Fixed

### Can result in data loss

* An ALTER TABLE, OPTIMIZE TABLE, or REPAIR TABLE on an Aria table of ROW\_FORMAT=PAGE (default) can fail or possibly corrupt the table, if the data file is bigger than 4GB. ([MDEV-34522](https://jira.mariadb.org/browse/MDEV-34522))
*   When executing an ALTER TABLE

    CHECK PARTITION FOR UPGRADE on a table, which was created by the same server version, and therefore does not need an upgrade, a following ALTER TABLE for the same table will result in a server crash. ([MDEV-32155](https://jira.mariadb.org/browse/MDEV-32155))

    **Can result in hang or crash**

    * When using SHOW CREATE DATABASE statement crashes the server with a database name containing Unicode characters, the server can crash ([MDEV-32376](https://jira.mariadb.org/browse/MDEV-32376))
    * For a partitioned table of type SPIDER where the remote connection is configured via CREATE SERVER, the server can crash if the server definition was removed via DROP SERVER ([MDEV-31475](https://jira.mariadb.org/browse/MDEV-31475))
    * When multiple threads try to load spider and to create a spider table, MariaDB can crash ([MDEV-32487](https://jira.mariadb.org/browse/MDEV-32487))
    * When enabling the PAGE\_COMPRESSED option for an InnoDB table created with INNODB\_DEFAULT\_ROW\_FORMAT=redundant, the server crashes. ([MDEV-34222](https://jira.mariadb.org/browse/MDEV-34222))
    * A query that plans to use the Rowid Filter optimization could crash the server if some factor causes it to terminate abnormally at a certain specific point in query optimization. Examples of such causes of termination are: ([MDEV-30651](https://jira.mariadb.org/browse/MDEV-30651))
      * Query being killed with KILL statement
      * Statement execution exceeding @@max\_statement\_time limit
    * When running a query with HAVING NOT column clause where the "column" is also used in the GROUP BY `{{ ... SELECT ... GROUP BY column ... HAVING NOT column}},` the server can crash. Other forms of HAVING clause were not affected ([MDEV-19520](https://jira.mariadb.org/browse/MDEV-19520))
    * An Auto-generated DELETE statement is added to the binary log for MEMORY tables, which can break replication. The DELETE cannot be executed in cases like missing triggers, which results in the replication being stopped. ([MDEV-25607](https://jira.mariadb.org/browse/MDEV-25607))
    * Replication fails when XA transactions are used where the replica has replicate\_do\_db set and the client has touched a different database when running DML such as inserts ([MDEV-33921](https://jira.mariadb.org/browse/MDEV-33921))
    * Replication fails in chain configurations if an XA transaction is replicated which results in an empty transaction on a replica. The XA START through XA PREPARE first phase of the transaction is not binlogged, yet the XA COMMIT is binlogged, which results in errors due to executing standalone XA COMMIT queries on replicas further in the chain. ([MDEV-33921](https://jira.mariadb.org/browse/MDEV-33921))
    * The server can crash for a query with a HAVING clause such that: ([MDEV-32293](https://jira.mariadb.org/browse/MDEV-32293)) ([MDEV-32424](https://jira.mariadb.org/browse/MDEV-32424)) ([MDEV-32304](https://jira.mariadb.org/browse/MDEV-32304)) ([MDEV-29363](https://jira.mariadb.org/browse/MDEV-29363))
    * It has several references to the same non-trivial constant (e.g., a subquery),
    * Condition pushdown optimization would try to move at least one of the references from HAVING clause into WHERE
    * If a query used a derived table (a CTE or a mergeable VIEW would work as well) and the WHERE clause compared columns of the derived table with the value of CHARSET() or COERCIBILITY() function, the query could produce wrong result, or crash. The cause was incorrect processing of these functions by [derived condition pushdown optimization](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/query-optimizations/optimizations-for-derived-tables/condition-pushdown-into-derived-table-optimization) ([MDEV-33010](https://jira.mariadb.org/browse/MDEV-33010))
    * With MariaDB Enterprise Custer a node can hang with the error: ([MDEV-31658](https://jira.mariadb.org/browse/MDEV-31658))

    ```
    "Deadlock found when trying to get lock; try restarting transaction, Error_code: 1213; handler error HA_ERR_LOCK_DEADLOCK; the event's master log FIRST, end_log_pos 1583, Internal MariaDB error code: 1213"
    ```

    **Can result in unexpected behavior**

    * Replicas only read the first 41 characters of MASTER\_PASSWORD from the master.info file. This leads to an access denied error for a replica on a server restart, if the password is > 41 characters long. ([MDEV-23857](https://jira.mariadb.org/browse/MDEV-23857))
    * Adding a partition in a spider table can lead to memory violation ([MDEV-29027](https://jira.mariadb.org/browse/MDEV-29027))
    * MariaDB Server still can allow new connections to be created when the Server got a fatal signal ([MDEV-34475](https://jira.mariadb.org/browse/MDEV-34475))
    * Slow warm-up for InnoDB as long as there are free pages in the buffer pool ([MDEV-34458](https://jira.mariadb.org/browse/MDEV-34458))
      * An InnoDB warm-up is not needed when using innodb\_buffer\_pool\_dump\_at\_shutdown=ON and innodb\_buffer\_pool\_load\_at\_startup=ON
      * A slowdown at run time has not been observed
    * mariadb-backup stores the password into the tool\_command setting in the file xtrabackup\_info, if the password is provided as command-line option ([MDEV-34434](https://jira.mariadb.org/browse/MDEV-34434))
    * The semi-sync binlog fail-over recovery process uses rpl\_semi\_sync\_slave\_enabled==TRUE as its condition to truncate a primary server's binlog, as it is anticipating the server to re-join a replication topology as a replica. However, for servers configured with both rpl\_semi\_sync\_master\_enabled=1, and rpl\_semi\_sync\_slave\_enabled=1, if a primary is just re-started (i.e., retaining its role as master), it can truncate its binlog to drop transactions which its replica(s) has already received, and executed. (MENT-2122)
      * If this happens, when the replica reconnects, its gtid\_slave\_pos can be ahead of the recovered primary's gtid\_binlog\_pos, resulting in an error state where the replica's state is ahead of the primary's.
      * Option --init-rpl-role will be used to define the initial role a server has. Possible options are MASTER and SLAVE, default MASTER . Setting it to SLAVE is now the condition for semi-sync recovery to truncate the binlog, This allows for both rpl\_semi\_sync\_master\_enabled, and rpl\_semi\_sync\_slave\_enabled to be set for a primary that is restarted, and no transactions will be lost, so long as --init-rpl-role is not set to SLAVE
    * Grouping operators referring to column aliases in unions inside derived tables can cause name resolution problems with prepared statements. ([MDEV-34506](https://jira.mariadb.org/browse/MDEV-34506))
    * Table mysql.gtid\_slave\_pos is replicated between two MariaDB Enterprise Cluster although wsrep\_gtid\_mode=OFF is set. ([MDEV-34170](https://jira.mariadb.org/browse/MDEV-34170))
    * wsrep\_sst\_mariadb-backup is using /tmp dir during SST instead of an user defined tmpdir ([MDEV-32158](https://jira.mariadb.org/browse/MDEV-32158))
    * The following misleading error message is shown with MariaDB Enterprise Cluster. Galera can mark user threads as high priority and so they can't be killed: ([MDEV-12008](https://jira.mariadb.org/browse/MDEV-12008))

    ```
    You are not the owner of the thread ....
    ```

    * Now the following error message is shown:

    ```
    This is a high priority thread/query and cannot be killed without compromising the consistency of the cluster
    ```

    * Executing an INSERT statement in PS mode having positional parameters bound with an array can result in an incorrect number of inserted rows in case there is a BEFORE INSERT trigger that executes yet another INSERT statement to put a copy of the row being inserted into some table. ([MDEV-24411](https://jira.mariadb.org/browse/MDEV-24411))
    * When using the asynchronous replication between two MariaDB Enterprise Cluster (Galera) environments, the domain id of the GTID can be wrongly set, or changed by Galera ([MDEV-32633](https://jira.mariadb.org/browse/MDEV-32633))

    **Related to performance**

    * Performance improvements for queries using a secondary indexes. (MENT-2126)
    * Slower query performance on some Linux systems because of a performance difference of the system call ftruncate'() to truncate data files, as ftruncate() causes a flush. MariaDB used "ftruncate" to periodically empty its temporary tables. Query plans with Split Materialized optimization are affected the most. (MENT-2125)
    * Using NAME\_CONST(), or executing query from the stored procedure and referring to a local variable, changes the plan, and may make execution slower ([MDEV-33971](https://jira.mariadb.org/browse/MDEV-33971))
    * `ALTER TABLE ... IMPORT TABLESPACE` can take unnecessarily long if a database uses a large number of tablespaces and the value inndb\_open\_files is lower than the number of existing table\_spaces ([MDEV-34670](https://jira.mariadb.org/browse/MDEV-34670))
    * Rowid Filter optimization cannot work with backward index scans. An attempt to run such a query plan will make the query perform very slowly. Fixed by disabling use of Rowid Filter if the optimizer decides to use a backward index scan. ([MDEV-33875](https://jira.mariadb.org/browse/MDEV-33875))

    **Changelog**

    * For the complete list of changes in this release, see the [changelog](changelog-for-mariadb-enterprise-server-10-6-19-15.md).

    **Platforms**

    In alignment to the [enterprise lifecycle](../enterprise-server-lifecycle.md), MariaDB Enterprise Server 10.6.19-15 is provided for:

    * AlmaLinux 8 (x86\_64, ARM64)
    * AlmaLinux 9 (x86\_64, ARM64)
    * Debian 11 (x86\_64, ARM64)
    * Debian 12 (x86\_64, ARM64)
    * Microsoft Windows (x86\_64) (MariaDB Enterprise Cluster excluded)
    * Red Hat Enterprise Linux 8 (x86\_64, ARM64)
    * Red Hat Enterprise Linux 9 (x86\_64, ARM64, PPC64LE)
    * Rocky Linux 8 (x86\_64, ARM64)
    * Rocky Linux 9 (x86\_64, ARM64)
    * SUSE Linux Enterprise Server 12 (x86\_64)
    * SUSE Linux Enterprise Server 15 (x86\_64, ARM64)
    * Ubuntu 20.04 (x86\_64, ARM64)
    * Ubuntu 22.04 (x86\_64, ARM64)
    * Ubuntu 24.04 (x86\_64, ARM64)

    Some components of MariaDB Enterprise Server might not support all platforms. For additional information, see [MariaDB Corporation Engineering Policies".](https://mariadb.com/engineering-policies)

## I

### Installation Instructions

* [MariaDB Enterprise Server ](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)[10](broken-reference)[.6](../11-4/whats-new-in-mariadb-enterprise-server-11-4.md)
* [Enterprise Cluster Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[10](broken-reference)[.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Primary/Replica Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/primary-replica)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [ColumnStore Object Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-object-storage)
* [ColumnStore Shared Local Storage Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/columnstore-shared-local-storage)
* [HTAP Topology with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and MariaDB Enterprise ColumnStore 23.02](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/htap)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)[ and Object Storage](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies/enterprise-server-with-columnstore-object-storage)
* [Single-Node Enterprise ColumnStore 23.02 with MariaDB Enterprise Server ](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[10](broken-reference)[.](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/single-node-topologies)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Sharded Topology with MariaDB Enterprise Server ](broken-reference)[10](broken-reference)[.](broken-reference)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)
* [Enterprise Spider Federated Topology with MariaDB Enterprise Server 10.](broken-reference)[6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/architecture/topologies/galera-cluster)

## Upgrade Instructions

* [Upgrade to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-from-to-specific-versions/upgrading-from-mariadb-10-5-to-mariadb-10-6)
* [Upgrade from MariaDB Community Server to MariaDB Enterprise Server 10.6](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/install-and-upgrade-mariadb/upgrading/upgrading-between-major-mariadb-versions)

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
