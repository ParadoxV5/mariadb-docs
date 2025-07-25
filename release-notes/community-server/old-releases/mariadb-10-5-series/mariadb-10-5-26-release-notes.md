# MariaDB 10.5.26 Release Notes

{% include "../../../.gitbook/includes/latest-10-5.md" %}

<a href="https://downloads.mariadb.org/mariadb/10.5.26/" class="button primary">Download</a> <a href="mariadb-10-5-26-release-notes.md" class="button secondary">Release Notes</a> <a href="../../changelogs/changelogs-mariadb-105-series/mariadb-10-5-26-changelog.md" class="button secondary">Changelog</a> <a href="what-is-mariadb-105.md" class="button secondary">Overview of 10.5</a>

**Release date:** 8 Aug 2024

[MariaDB 10.5](what-is-mariadb-105.md) is a previous _stable_ series of MariaDB, [maintained until](https://mariadb.org/about/#maintenance-policy) June 2025. It is an evolution of [MariaDB 10.4](../release-notes-mariadb-10-4-series/what-is-mariadb-104.md) with several entirely new features not found anywhere else and with backported and reimplemented features from MySQL.

[MariaDB 10.5.26](mariadb-10-5-26-release-notes.md) is a [_**Stable (GA)**_](../../about/release-criteria.md) release.

Thanks, and enjoy MariaDB!

## Notable Items

### Storage Engines

#### InnoDB

* Alter operation on redundant table aborts the server ([MDEV-34222](https://jira.mariadb.org/browse/MDEV-34222))
* MariaDB crashes with SIGILL because the OS does not support AVX512 ([MDEV-34565](https://jira.mariadb.org/browse/MDEV-34565))
* InnoDB: Failing assertion: `stat_n_leaf_pages > 0` in `ha_innobase::estimate_rows_upper_bound` ([MDEV-34474](https://jira.mariadb.org/browse/MDEV-34474))

#### Aria

* Fix [Aria](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/aria) index corruption when doing a REPAIR TABLE that has a size of over 4G ([MDEV-34522](https://jira.mariadb.org/browse/MDEV-34522))

#### Spider

* UBSAN: runtime error: applying non-zero offset in `spider_free_mem` and SIGSEGV in `spider_free_mem` on SELECT ([MDEV-31475](https://jira.mariadb.org/browse/MDEV-31475))
* SIGSEGV in `ha_resolve_storage_engine_name`, UBSAN: runtime error: index 4294967295 out of bounds for type 'st\_plugin\_int \*\[64]' ([MDEV-32487](https://jira.mariadb.org/browse/MDEV-32487))
* SIGSEGV in `spider_db_conn::fin_loop_check`, and ASAN: heap-use-after-free in `spider_db_mbase::fin_loop_check` on SHOW TABLE STATUS ([MDEV-34541](https://jira.mariadb.org/browse/MDEV-34541))
* SIGSEGV in `ha_spider::lock_tables` on BEGIN after table lock ([MDEV-29962](https://jira.mariadb.org/browse/MDEV-29962))
* SIGSEGV in `spider_conn_first_link_idx` and others on DELETE, INSERT and SELECT ([MDEV-32492](https://jira.mariadb.org/browse/MDEV-32492))
* Spider: Crashes, asserts, hangs, memory corruptions and ASAN heap-use-after-free's ([MDEV-27902](https://jira.mariadb.org/browse/MDEV-27902))
* Spider: `@@insert_id 128` to TINYINT: Assertion \`\`!is\_set() || (m\_status == DA\_OK\_BULK && is\_bulk\_op())'\` failed. ([MDEV-28105](https://jira.mariadb.org/browse/MDEV-28105))
* Server crashes when calling spider UDF after `aria_encrypt_tables` is enabled ([MDEV-34682](https://jira.mariadb.org/browse/MDEV-34682))

### Partitioning

* MariaDB Server crashes with ill-formed partitions ([MDEV-32155](https://jira.mariadb.org/browse/MDEV-32155))
* SIGSEGV in `parse_engine_part_options` on INSERT, SELECT or ALTER ([MDEV-34421](https://jira.mariadb.org/browse/MDEV-34421))
* Assertion \`\`auto\_increment\_value'`failed in`ha\_partition::info\` on INSERT into MEMORY table ([MDEV-24610](https://jira.mariadb.org/browse/MDEV-24610))

### Character Sets

* On startup: UBSAN: applying zero offset to null pointer in `my_copy_fix_mb` from `strings/ctype-mb.c` and other locations ([MDEV-34226](https://jira.mariadb.org/browse/MDEV-34226))
* On startup: UBSAN: runtime error: applying zero offset to null pointer in `skip_trailing_space` and `my_hash_sort_utf8mb3_general1400_nopad_as_ci` ([MDEV-34187](https://jira.mariadb.org/browse/MDEV-34187))
* SHOW CREATE DATABASE statement crashes the server when db name contains some unicode characters, ASAN stack-buffer-overflow ([MDEV-32376](https://jira.mariadb.org/browse/MDEV-32376))
* Wrong result set with `utf8mb4_danish_ci` and BNLH join ([MDEV-34417](https://jira.mariadb.org/browse/MDEV-34417))

### Optimizer

* On startup: UBSAN: runtime error: applying non-zero offset in `JOIN::make_aggr_tables_info` in sql/sql\_select.cc ([MDEV-34227](https://jira.mariadb.org/browse/MDEV-34227))
* Crash after killing query while it is processed by `test_quick_select` ([MDEV-30651](https://jira.mariadb.org/browse/MDEV-30651))
* Extend condition normalization to include `'NOT a'` ([MDEV-19520](https://jira.mariadb.org/browse/MDEV-19520))
* Constant subquery causing a crash in pushdown optimization ([MDEV-29363](https://jira.mariadb.org/browse/MDEV-29363))
* Crash when pushing condition with CHARSET()/COERCIBILITY() into derived table ([MDEV-33010](https://jira.mariadb.org/browse/MDEV-33010))
* 2nd execution name resolution problem with pushdown into unions ([MDEV-34506](https://jira.mariadb.org/browse/MDEV-34506))
* Assertion \`\`(key\_part->key\_part\_flag & 4) == 0'\` failed key\_hashnr ([MDEV-34580](https://jira.mariadb.org/browse/MDEV-34580))
* Crash caused by query containing constant having clause ([MDEV-23983](https://jira.mariadb.org/browse/MDEV-23983))
* `ORDER BY DESC` causes ROWID Filter optimization performance degradation ([MDEV-33875](https://jira.mariadb.org/browse/MDEV-33875))

### [Replication](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication)

* Auto-generated [DELETE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-manipulation/changing-deleting-data/delete) from [HEAP](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/storage-engines/memory-storage-engine) table no longer breaks replication ([MDEV-25607](https://jira.mariadb.org/browse/MDEV-25607))
* Fix replication failure when [XA transactions](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/transactions/xa-transactions) are used where the replica has [replicate\_do\_db](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/standard-replication/replication-and-binary-log-system-variables#replicate_do_db) set and the client has touched a different database when running DML such as inserts. ([MDEV-33921](https://jira.mariadb.org/browse/MDEV-33921))
* Fix replication error when [CHANGE MASTER TO](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/administrative-sql-statements/replication-statements/change-master-to) is used in conjunction with a password longer than 41 ascii characters ([MDEV-23857](https://jira.mariadb.org/browse/MDEV-23857))

### Backup

* Hide password passed on commandline from `xtrabackup_info` ([MDEV-34434](https://jira.mariadb.org/browse/MDEV-34434))

### Galera

* [Galera](https://app.gitbook.com/o/diTpXxF5WsbHqTReoBsS/s/3VYeeVGUV4AMqrA3zwy7/) updated to 26.4.19
  * NOTE: Includes increasing the GCS protocol version, which prevents downgrades of individual nodes in the cluster as soon as all nodes have been updated
* `galera_gtid_2_cluster`: Assertion \`\`thd->wsrep\_next\_trx\_id() != (0x7fffffffffffffffLL \* 2ULL + 1)'\` ([MDEV-32633](https://jira.mariadb.org/browse/MDEV-32633))
* table `gtid_slave_pos` entries never been deleted with `wsrep_gtid_mode = 0` ([MDEV-34170](https://jira.mariadb.org/browse/MDEV-34170))
* Change error code for Galera unkillable threads ([MDEV-12008](https://jira.mariadb.org/browse/MDEV-12008))
* 10.11.8 cluster becomes inconsistent when using composite primary key and partitioning ([MDEV-34269](https://jira.mariadb.org/browse/MDEV-34269))
* `wsrep_sst_mariadb-backup` use `/tmp` dir during SST rather then user defined `tmpdir` ([MDEV-32158](https://jira.mariadb.org/browse/MDEV-32158))

### Error Log

* [server\_uid](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/server-system-variables#server_uid) system variable added, and value added to the [error log](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-management/server-monitoring-logs/error-log) at startup ([MDEV-34494](https://jira.mariadb.org/browse/MDEV-34494))

### General

* As per the [MariaDB Deprecation Policy](../../about/platform-deprecation-policy.md), this will be the last release of [MariaDB 10.5](what-is-mariadb-105.md) for Debian 10 "Buster", and RHEL/CentOS 7
* [IMPORT TABLESPACE](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/data-definition/alter/alter-table#import-tablespace) no longer unnecessarily traverses tablespaces list ([MDEV-34670](https://jira.mariadb.org/browse/MDEV-34670))
* Fix unknown variable `defaults-group-suffix=` with [mariadb-secure-installation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/deployment-tools/mariadb-secure-installation) ([MDEV-33265](https://jira.mariadb.org/browse/MDEV-33265))
* [mariadb-install-db](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/deployment-tools/mariadb-install-db) no longer hangs on macOS ([MDEV-34129](https://jira.mariadb.org/browse/MDEV-34129))
* Control over memory allocated for SP/PS ([MDEV-14959](https://jira.mariadb.org/browse/MDEV-14959))
* [Triggers](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/server-usage/triggers-events/triggers) now work correctly with bulk insert ([MDEV-24411](https://jira.mariadb.org/browse/MDEV-24411))
* Fix assertion \`\`table->field\[0]->ptr >= table->record\[0] && table->field\[0]->ptr <= table->record\[0] + table->s->reclength'`failed in`void handler::assert\_icp\_limitations(uchar\*)\` ([MDEV-34632](https://jira.mariadb.org/browse/MDEV-34632))
* [sandbox mode](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/mariadb-client/mariadb-command-line-client#-sandbox) - now compatible with [--binary-mode](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/mariadb-client/mariadb-command-line-client#-binary-mode) ([MDEV-34203](https://jira.mariadb.org/browse/MDEV-34203))

### Security

* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * CVE-`-``#`

## Changelog

For a complete list of changes made in [MariaDB 10.5.26](mariadb-10-5-26-release-notes.md), with links to detailed\
information on each push, see the [changelog](../../changelogs/changelogs-mariadb-105-series/mariadb-10-5-26-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.5.26](mariadb-10-5-26-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-11-6-1-11-5-2-11-4-3-11-2-5-11-1-6-10-11-9-10-6-19-and-10-5-26-now-available/).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
