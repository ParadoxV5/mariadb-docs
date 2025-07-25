# Connector/J 3.1.2 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](mariadb-connector-j-3-1-2-release-notes.md)[Changelog](../changelogs/3.1/mariadb-connector-j-3-1-2-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 24 Jan 2023

MariaDB Connector/J 3.1.2 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Notable Changes

* [CONJ-1042](https://jira.mariadb.org/browse/CONJ-1042) fix DatabaseMetaData.getColumns() on old server version (< MySQL 5.6.4 and < [MariaDB 5.3.0](../../../community-server/old-releases/release-notes-mariadb-5-3-series/mariadb-530-release-notes.md))

## Bug fixed

* [CONJ-1040](https://jira.mariadb.org/browse/CONJ-1040) possible ConcurrentModificationException when parsing properties when connecting
* [CONJ-1041](https://jira.mariadb.org/browse/CONJ-1041) possible ArrayIndexOutOfBoundsException when writing a parameter to socket pre-buffer when pre-buffer is exactly 16M

## Changelog

For a complete list of changes made in MariaDB Connector/J 3.1.2, with links to detailed\
information on each push, see the [changelog](../changelogs/3.1/mariadb-connector-j-3-1-2-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
