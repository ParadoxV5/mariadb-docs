# Connector/C 3.4.4 Release Notes

The most recent [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/C is:[**MariaDB Connector/C 3.4.5**](mariadb-connector-c-3-4-5-release-notes.md)

[Download](https://mariadb.com/downloads/connectors)[Release Notes](mariadb-connector-c-3-4-4-release-notes.md)[Changelog](../changelogs/mariadb-connectorc-3-4-changelogs/mariadb-connector-c-3-4-4-changelog.md)[About MariaDB Connector/C](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-c/README.md)

**Release date:** 11 Feb 2025

This is a [_**Stable (GA)**_](../../../community-server/about/release-criteria.md) release of MariaDB\
Connector/C, formerly known as MariaDB Client Library for C.

**For a description of this library see the**[**MariaDB Connector/C**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-c) **page.**

## Notable changes

* Added support for setting zstd compression level via mysql\_optionsv parameter MYSQL\_OPT\_ZSTD\_COMPRESSION\_LEVEL.

## Issues fixed:

* [CONC-693](https://jira.mariadb.org/browse/CONC-693): Fix SSL\_read/write return value checking in ma\_tls\_async\_check\_result (Kudos to Joshua Hunt for contributing this fix)
* [CONC-589](https://jira.mariadb.org/browse/CONC-589): First query fails after reconnect
* [CONC-711](https://jira.mariadb.org/browse/CONC-711): Ubsan and Asan fixes
* [CONC-709](https://jira.mariadb.org/browse/CONC-709): Fix crash when sending NULL\_LENGTH in field description
* [CONC-708](https://jira.mariadb.org/browse/CONC-708): Fix possible buffer overflow in ma\_read\_ok\_packet
* [CONC-748](https://jira.mariadb.org/browse/CONC-748): Added support for TLSv1.3 ciphers (GnuTLS)
* [CONC-756](https://jira.mariadb.org/browse/CONC-756): Parsec plugin not unloaded during mtr-test run
* [CONC-739](https://jira.mariadb.org/browse/CONC-739): prepared statement support AUTO\_SEC\_PART\_DIGITS

## Changelog

For a list of changes made in this release, with links to detailed information\
on each push, see the [changelog](../changelogs/mariadb-connectorc-3-4-changelogs/mariadb-connector-c-3-4-4-changelog.md).

{% include "../../../.gitbook/includes/announce.md" %}

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/7hzG0V6AUK8DqF4oiVaW/" %}

{% @marketo/form formid="4316" formId="4316" %}
