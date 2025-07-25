# MariaDB 10.4.18 Release Notes

The most recent release of [MariaDB 10.4](https://mariadb.com/docs/release-notes/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-4-series) is:[**MariaDB 10.4.34**](mariadb-10-4-34-release-notes.md) Stable (GA) [Download Now](https://downloads.mariadb.org/mariadb/10.4.34/)

[Download 10.4.18](https://downloads.mariadb.org/mariadb/10.4.18/)[Release Notes](mariadb-10418-release-notes.md)[Changelog](../../changelogs/changelogs-mariadb-10-4-series/mariadb-10418-changelog.md)[Overview of 10.4](https://mariadb.com/docs/release-notes/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-4-series/what-is-mariadb-104)

**Release date:** 22 Feb 2021

**Last month long-time MariaDB VP of Engineering, Rasmus Johansson, passed due to complications from cancer. His loss has been felt keenly by the whole MariaDB team. Our thoughts are with his family during this difficult time and this release is dedicated to his memory.**

[MariaDB 10.4](https://mariadb.com/docs/release-notes/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-4-series) is the previous _stable_ series of MariaDB. It is an evolution\
of [MariaDB 10.3](../release-notes-mariadb-10-3-series/what-is-mariadb-103.md) with several entirely new features not found anywhere else\
and with backported and reimplemented features from MySQL.

[MariaDB 10.4.18](mariadb-10418-release-notes.md) is a [_**Stable (GA)**_](../../about/release-criteria.md) release.

**For an overview of** [**MariaDB 10.4**](https://mariadb.com/docs/release-notes/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-4-series) **see the**[**What is MariaDB 10.4?**](https://mariadb.com/docs/release-notes/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-4-series/what-is-mariadb-104) **page.**

Thanks, and enjoy MariaDB!

## Notable Changes

### InnoDB

* [MDEV-24188](https://jira.mariadb.org/browse/MDEV-24188) - Hang in buf\_page\_create() after reusing a previously freed page
* [MDEV-24275](https://jira.mariadb.org/browse/MDEV-24275) - [InnoDB persistent stats](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/query-optimizations/statistics-for-optimizing-queries/innodb-persistent-statistics) analyze forces full scan forcing lock crash
* [MDEV-24449](https://jira.mariadb.org/browse/MDEV-24449) - Corruption of system tablespace or last recovered page

### Galera

* [Galera](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/galera-cluster/README.md) updated to 26.4.7
* [MDEV-23328](https://jira.mariadb.org/browse/MDEV-23328) - Server hang due to Galera lock conflict resolution
* [MDEV-23851](https://jira.mariadb.org/browse/MDEV-23851) - BF-BF Conflict issue because of UK GAP locks
* [MDEV-20717](https://jira.mariadb.org/browse/MDEV-20717) - Plugin system variables and activation options can break [mysqld --wsrep\_recover](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_recover)
* [MDEV-24469](https://jira.mariadb.org/browse/MDEV-24469) - Assertion `active() == false` failed with "XA START.."
* [MDEV-23647](https://jira.mariadb.org/browse/MDEV-23647) - Garbd can't initiate SST anymore in 10.5
* [MDEV-25179](https://jira.mariadb.org/browse/MDEV-25179) - [wsrep\_provider](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_provider) and [wsrep\_notify\_cmd](https://app.gitbook.com/s/3VYeeVGUV4AMqrA3zwy7/reference/galera-cluster-system-variables#wsrep_notify_cmd) system variables are now read-only

### Replication

* [MDEV-8134](https://jira.mariadb.org/browse/MDEV-8134) - relay-log is corrected to rotate past 999999
* [MDEV-23033](https://jira.mariadb.org/browse/MDEV-23033) - fixed slave applier for row-based events with FK constraints on virtual columns
* [MDEV-4633](https://jira.mariadb.org/browse/MDEV-4633) - Relay\_Log\_Space of Show-Slave-Status is made thread-safe
* [MDEV-10272](https://jira.mariadb.org/browse/MDEV-10272) - add master host/port info to slave thread exit messages
* [MDEV-23846](https://jira.mariadb.org/browse/MDEV-23846) - improves [mysqlbinlog](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/logging-tools/mariadb-binlog) error message issuing

### Misc

* [MDEV-24122](https://jira.mariadb.org/browse/MDEV-24122) - anomalies in mysql.user tables on previously 5.7 MySQL versions corrected
* Binary tarballs now use WolfSSL v4.6.0
* [MDEV-23630](https://jira.mariadb.org/browse/MDEV-23630) - [mysqldump --system](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/clients-and-utilities/legacy-clients-and-utilities/mysqldump) option
* Fixes for the following [security vulnerabilities](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/security/securing-mariadb/security):
  * [CVE-2021-27928](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-27928)

## Changelog

For a complete list of changes made in [MariaDB 10.4.18](mariadb-10418-release-notes.md), with links to detailed\
information on each push, see the [changelog](../../changelogs/changelogs-mariadb-10-4-series/mariadb-10418-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.4.18](mariadb-10418-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-5-9-10-4-18-10-3-28-and-10-2-37-now-available/).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
