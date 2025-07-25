# MariaDB Connector/J 3.5.1 Changelog

{% include "../../../../.gitbook/includes/latest-java.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/java8-connector)[Release Notes](../../3.5/mariadb-connector-j-3-5-1-release-notes.md)[Changelog](mariadb-connector-j-3-5-1-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-j/README.md)

**Release date:** 20 Nov 2024

For the highlights of this release, see the[release notes](../../3.5/mariadb-connector-j-3-5-1-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-j) you can view more\
details of the revision and view diffs of the code modified in that revision.

* [Revision #8acdd273](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8acdd273) \[misc] benchmark handling bcpkix-jdk18on signed JAR
* [Revision #99a46492](https://github.com/mariadb-corporation/mariadb-connector-j/commit/99a46492) \[misc] adding benchmark parsec
* [Revision #04170a1e](https://github.com/mariadb-corporation/mariadb-connector-j/commit/04170a1e) \[misc] update travis windows testing to java 17
* [Revision #99d585b9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/99d585b9) - bump 3.5.1
* [Revision #8c8200fd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/8c8200fd) - \[[CONJ-1213](https://jira.mariadb.org/browse/CONJ-1213)] sql command ending with semicolon and trailing space are not using bulk
* [Revision #b7f38ea9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b7f38ea9) - \[misc] javadoc formatting correction
* [Revision #3f1706ed](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3f1706ed) - \[misc] correct javadoc entries
* [Revision #e3df57b1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/e3df57b1) - \[misc] permit java 11 testing
* [Revision #147a08a2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/147a08a2) - \[misc] parsec SSL fingerprint test correction
* [Revision #da6a56ce](https://github.com/mariadb-corporation/mariadb-connector-j/commit/da6a56ce) - \[misc] parsec fingerprint hash using either java 15 or BouncyCastle
* [Revision #ce37c467](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ce37c467) - Merge branch 'parsec-ssl' into develop
* [Revision #2194616b](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2194616b) - \[misc] improve fingerprint validation error message
* [Revision #194479c9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/194479c9) - \[[CONJ-1193](https://jira.mariadb.org/browse/CONJ-1193)] permit Zero-Config SSL for parsec authentication
* [Revision #912d9e76](https://github.com/mariadb-corporation/mariadb-connector-j/commit/912d9e76) - \[misc] suppress deprecation warning
* [Revision #734e7de1](https://github.com/mariadb-corporation/mariadb-connector-j/commit/734e7de1) - \[misc] ensure not having race condition on authentication plugin states
* [Revision #603771f9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/603771f9) - \[misc] avoid useless truncation warning
* [Revision #cc8c3354](https://github.com/mariadb-corporation/mariadb-connector-j/commit/cc8c3354) - \[misc] ensure setting generic type
* [Revision #bd7cd105](https://github.com/mariadb-corporation/mariadb-connector-j/commit/bd7cd105) - \[misc] improve logging clarity for BULK
* [Revision #3871fdd2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/3871fdd2) - \[[CONJ-1211](https://jira.mariadb.org/browse/CONJ-1211)] jdbc 4.3 enquoteIdentifier missing validation
* [Revision #75038b84](https://github.com/mariadb-corporation/mariadb-connector-j/commit/75038b84) - \[misc] ensure permitting primary/replica client depending on configuration
* [Revision #089cbecd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/089cbecd) - \[misc] test stability improvement
* [Revision #c47e5852](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c47e5852) - \[misc] permits JDBC enquoteIdentifier and enquoteLiteral use at static level
* [Revision #b8c28b70](https://github.com/mariadb-corporation/mariadb-connector-j/commit/b8c28b70) - \[misc] code coverage not throwing error on patch debug level
* [Revision #1bafd3ff](https://github.com/mariadb-corporation/mariadb-connector-j/commit/1bafd3ff) - Merge branch 'A248-require-static-waffle-jna' into develop #185
* [Revision #10c3ad34](https://github.com/mariadb-corporation/mariadb-connector-j/commit/10c3ad34) - Merge branch 'require-static-waffle-jna' of [mariadb-connector-j](https://github.com/A248/mariadb-connector-j) into A248-require-static-waffle-jna
* [Revision #eae949a9](https://github.com/mariadb-corporation/mariadb-connector-j/commit/eae949a9) - \[[CONJ-1196](https://jira.mariadb.org/browse/CONJ-1196)] setObject on java.util.Date was considered was a java.sql.Date and truncate hour/minutes/seconds/ms while it must be considered like a java.sql.Timestamp
* [Revision #472581d0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/472581d0) - \[misc] test correction for failover
* [Revision #9c2db3be](https://github.com/mariadb-corporation/mariadb-connector-j/commit/9c2db3be) - \[[CONJ-1207](https://jira.mariadb.org/browse/CONJ-1207)] new High Availability option : load-balance-read
* [Revision #65b49030](https://github.com/mariadb-corporation/mariadb-connector-j/commit/65b49030) - \[misc] code style correction
* [Revision #512cd124](https://github.com/mariadb-corporation/mariadb-connector-j/commit/512cd124) - \[[CONJ-1193](https://jira.mariadb.org/browse/CONJ-1193)] parsec authentication implementation
* [Revision #ce9b23c2](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ce9b23c2) - \[[CONJ-1208](https://jira.mariadb.org/browse/CONJ-1208)] ensure not using pipelining prepare + execute for mysql server
* [Revision #4738d1d0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/4738d1d0) - \[misc] code style correction
* [Revision #ca5b3767](https://github.com/mariadb-corporation/mariadb-connector-j/commit/ca5b3767) - \[misc] test addition
* [Revision #64c410c3](https://github.com/mariadb-corporation/mariadb-connector-j/commit/64c410c3) - \[[CONJ-1208](https://jira.mariadb.org/browse/CONJ-1208)] permit bulk for INSERT ON DUPLICATE KEY UPDATE commands
* [Revision #53976874](https://github.com/mariadb-corporation/mariadb-connector-j/commit/53976874) - bump 3.5.1-SNAPSHOT
* [Revision #2eacf8a0](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2eacf8a0) - \[misc] removing remnant of ES23 version
* [Revision #2a3a5ecd](https://github.com/mariadb-corporation/mariadb-connector-j/commit/2a3a5ecd) - Merge branch 'develop'
* [Revision #13e82eb7](https://github.com/mariadb-corporation/mariadb-connector-j/commit/13e82eb7) - Merge pull request #195 from Piroro-hs/fix-pom-license-id
* [Revision #10dded20](https://github.com/mariadb-corporation/mariadb-connector-j/commit/10dded20) - Merge pull request #197 from markus456/patch-1
* [Revision #421a3a5c](https://github.com/mariadb-corporation/mariadb-connector-j/commit/421a3a5c) - \[misc] changing capability name EXTENDED\_TYPE\_INFO to EXTENDED\_METADATA, in order to correspond to server and other connectors
* [Revision #c90f656a](https://github.com/mariadb-corporation/mariadb-connector-j/commit/c90f656a) - \[misc] remove test condition specific for ES 23.08
* [Revision #892d1157](https://github.com/mariadb-corporation/mariadb-connector-j/commit/892d1157) - Use 32760 as the "unused" port number

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
