# Connector/J 2.7.3 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/#connectors)[Release Notes](mariadb-connector-j-273-release-notes.md)[Changelog](../changelogs/2.7/mariadb-connector-j-273-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 12 May 2021

MariaDB Connector/J 2.7.3 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Notable Change

* [CONJ-883](https://jira.mariadb.org/browse/CONJ-883) using unix socket, hostname is not mandatory anymore

## Bugs Fixed

* [CONJ-619](https://jira.mariadb.org/browse/CONJ-619) Multiple batch update fails after LOAD DATA LOCAL INFILE
* [CONJ-854](https://jira.mariadb.org/browse/CONJ-854) LOAD XML INFILE breaks when using LOCAL
* [CONJ-855](https://jira.mariadb.org/browse/CONJ-855) throwing more specific exception for updatable result-set that can not be updated by ResultSet
* [CONJ-857](https://jira.mariadb.org/browse/CONJ-857) Avoid using mysql.proc table
* [CONJ-864](https://jira.mariadb.org/browse/CONJ-864) includeThreadDumpInDeadlockExceptions always includes the thread dump, even when it is not a deadlock exception
* [CONJ-866](https://jira.mariadb.org/browse/CONJ-866) long binary parsing improvement
* [CONJ-871](https://jira.mariadb.org/browse/CONJ-871) OSGi: Missing Import-Package in Connector/J bundle (javax.sql.rowset.serial)
* [CONJ-878](https://jira.mariadb.org/browse/CONJ-878) option serverSslCert file location
* [CONJ-880](https://jira.mariadb.org/browse/CONJ-880) metadata query performance correction
* [CONJ-858](https://jira.mariadb.org/browse/CONJ-858) Properties.put with object that differ from String supported even if use is not recommended
* [CONJ-861](https://jira.mariadb.org/browse/CONJ-861) executeBatch must not clear last parameter value.

## Changelog

For a complete list of changes made in MariaDB Connector/J 2.7.3, with links to detailed\
information on each push, see the [changelog](../changelogs/2.7/mariadb-connector-j-273-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
