# MariaDB 10.6.14 Release Notes

{% include "../../.gitbook/includes/latest-10-6.md" %}

<a href="https://downloads.mariadb.org/mariadb/10.6.14/" class="button primary">Download</a> <a href="mariadb-10-6-14-release-notes.md" class="button secondary">Release Notes</a> <a href="../changelogs/changelogs-mariadb-106-series/mariadb-10-6-14-changelog.md" class="button secondary">Changelog</a> <a href="what-is-mariadb-106.md" class="button secondary">Overview of 10.6</a>

**Release date:** 7 Jun 2023

Warning: This version can cause InnoDB file corruption under high I/O-bound load. Stick to an earlier release, or upgrade to a more recent release, if possible. See [MDEV-31767](https://jira.mariadb.org/browse/MDEV-31767).

[MariaDB 10.6](what-is-mariadb-106.md) is the current long-term series of MariaDB, [maintained until](https://mariadb.org/about/#maintenance-policy) July 2026. It is an evolution of [MariaDB 10.5](../old-releases/mariadb-10-5-series/what-is-mariadb-105.md) with several entirely new features.

[MariaDB 10.6.14](mariadb-10-6-14-release-notes.md) is a [_**Stable (GA)**_](../about/release-criteria.md) release.

Thanks, and enjoy MariaDB!

## Notable Items

### InnoDB

* Server crashes in st\_join\_table::choose\_best\_splitting ([MDEV-31403](https://jira.mariadb.org/browse/MDEV-31403))
* Crash with condition pushable into derived and containing outer reference ([MDEV-31240](https://jira.mariadb.org/browse/MDEV-31240))
* InnoDB does not free UNDO after the fix of [MDEV-30671](https://jira.mariadb.org/browse/MDEV-30671) ([MDEV-31234](https://jira.mariadb.org/browse/MDEV-31234))
* InnoDB hang fixes ([MDEV-31158](https://jira.mariadb.org/browse/MDEV-31158), [MDEV-31343](https://jira.mariadb.org/browse/MDEV-31343), [MDEV-31350](https://jira.mariadb.org/browse/MDEV-31350))
* [Innodb\_buffer\_pool\_read\_requests](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/ha-and-performance/optimization-and-tuning/system-variables/innodb-status-variables#innodb_buffer_pool_read_requests) is not updated correctly ([MDEV-31309](https://jira.mariadb.org/browse/MDEV-31309))
* InnoDB monitor trx\_rseg\_history\_len was accidentally disabled by default ([MDEV-31308](https://jira.mariadb.org/browse/MDEV-31308))
* Revert "[MDEV-30473](https://jira.mariadb.org/browse/MDEV-30473) : Do not allow GET\_LOCK() / RELEASE\_LOCK() in cluster"

### Optimizer

* Crash with condition pushable into derived and containing outer reference ([MDEV-31403](https://jira.mariadb.org/browse/MDEV-31403) [MDEV-31240](https://jira.mariadb.org/browse/MDEV-31240))
* Crash with [EXPLAIN EXTENDED](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/sql-statements/administrative-sql-statements/analyze-and-explain-statements/explain) for multi-table update of system table ([MDEV-31224](https://jira.mariadb.org/browse/MDEV-31224))

## Changelog

For a complete list of changes and bugfixes made in [MariaDB 10.6.14](mariadb-10-6-14-release-notes.md), with links to detailed\
information on each push, see the [changelog](../changelogs/changelogs-mariadb-106-series/mariadb-10-6-14-changelog.md).

## Contributors

For a full list of contributors to [MariaDB 10.6.14](mariadb-10-6-14-release-notes.md), see the [MariaDB Foundation release announcement](https://mariadb.org/mariadb-10-11-4-10-10-5-10-9-7-10-6-14-10-5-21-10-4-30-now-available/).

{% include "../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
