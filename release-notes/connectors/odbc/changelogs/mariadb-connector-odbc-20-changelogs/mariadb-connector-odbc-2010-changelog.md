# Connector/ODBC 2.0.10 Changelog

The most recent [_**Stable**_](../../../../community-server/about/release-criteria.md) _**(GA)**_ release of MariaDB Connector/ODBC is:[**MariaDB Connector/ODBC 3.2.5**](../../mariadb-connector-odbc-3-2-release-notes/mariadb-connector-odbc-3-2-5-release-notes.md)

[Download](https://downloads.mariadb.org/connector-odbc/2.0.10)[Release Notes](../../mariadb-connector-odbc-20-release-notes/mariadb-connector-odbc-2010-release-notes.md)[Changelog](mariadb-connector-odbc-2010-changelog.md)[About MariaDB Connector/ODBC](https://github.com/mariadb-corporation/docs-release-notes/blob/test/en/about-mariadb-connector-odbc/README.md)

**Release date:** 11 Apr 2016

For the highlights of this release, see the[release notes](../../mariadb-connector-odbc-20-release-notes/mariadb-connector-odbc-2010-release-notes.md).

The revision number links will take you to the revision's page on GitHub. On[GitHub](https://github.com/MariaDB/mariadb-connector-odbc) you can view more details of the revision and view diffs of the code modified in that revision.

* [Revision #98da8ac](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/98da8ac)\
  2016-04-06 01:01:31 +0200
  * Changed version quality in the cmake config file
* [Revision #ab99611](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/ab99611)\
  2016-04-06 00:38:40 +0200\
  \*
  1. Fixed build on windows - removed some dependencies from maodbcs project, introduced file(ma\_common.c) where I moved all stuff required by both libraries. 2) Fixed bug [ODBC-32](https://jira.mariadb.org/browse/ODBC-32)(and around it), and added testcase for it 3) Corrected couple of testcases, added one for the issue#3 on github 4) Fixed some more merge errors
* [Revision #a076fdb](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/a076fdb)\
  2016-04-04 01:44:21 +0300
  * Resolved problem with SQLBindParam under UnixODBC. Fixed earlier introduced regression in SQLGetData by chunks offset calculation. Dirty hacked fix for some unicode tests - test strings could not be converted properly from utf32le Fixed couple of tests in result1 and unicode
* [Revision #f9e9dfa](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/f9e9dfa)\
  2016-03-29 18:41:56 +0200
  * Fixed several testcases in 'cursor' and 'info' suites
* [Revision #cf55b3c](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/cf55b3c)\
  2016-03-23 20:20:48 +0200
  * Fix of several memory leaks and of some previous merge mistakes.\
    There was a leak in the SQLConnect - uid/pwd strings were leaked.\
    Leak in the internal routine re-getting current db name.\
    Some SQLSetPos operations leaked\
    Some fields in Stmt and descriptors were leaked in some conditions.
* [Revision #ffa6d03](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/ffa6d03)\
  2016-03-22 01:20:51 +0100
  * Merge branch 'master' into [ODBC-2](https://jira.mariadb.org/browse/ODBC-2).0
* [Revision #91825b7](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/91825b7)\
  2016-03-11 12:00:30 +0100
  * Made possible to turn off ssl certificate verification(for the case when it is turned on by default)
* [Revision #9e8bca5](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/9e8bca5)\
  2016-03-04 23:34:59 +0100
  * Changed the dialog to use IFileDialog instead of SHBrowseForFolder Added push buttons for file/folder dialog opening, where they were missing
* [Revision #d47f21d](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/d47f21d)\
  2016-02-29 22:30:32 +0100
  * Fix + test case(s) for the [ODBC-27](https://jira.mariadb.org/browse/ODBC-27). Also fixes other things around dialog invocation logic. In particular for COMPLETE/\_REQUIRED completion types. Change(or call it a fix) in connection string parsing - if DRIVER keyword is given, DSN(if given too) won't be expanded. I think that is what specs say.
* [Revision #734531f](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/734531f)\
  2016-02-10 16:33:24 +0100
  * Connection string processing - many changes/fixes, that among others, should allow to fix [ODBC-30](https://jira.mariadb.org/browse/ODBC-30)(after merging to 2.0) Connection string is now parsed, then, if DSN is present, DSN info is read and connection string is parsed again. Introduced dependencies between fields, like setting TCPIP resets NamedPipe. Introducing connstring.c tests suite, which compiles in ma\_dsn.c, to effectively test connection string operations. Also adding interactive.c for interactive tests, i.e. tests of connector behaviors when dialog invocation is involved. BUILD\_INTERACTIVE\_TESTS and USE\_INTERACTIVE\_TESTS control whether to build and run those tests automatically.
* [Revision #f48d3a5](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/f48d3a5)\
  2016-01-17 00:28:13 +0100
  * Fix of the bug in connection string parsing - if options were set by their individual name(currently these are NO\_PROMPT, NamedPipe and AUTO\_RECONNECT, they would not have any effect. Added calling convention to DSNPrompt function pointer type definition
* [Revision #ff29265](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/ff29265)\
  2016-01-16 15:53:37 +0100
  * Fix and the testcase for the part of [ODBC-29](https://jira.mariadb.org/browse/ODBC-29) - the problem with query with leading >1 spaces. Connector trimmed the query, but did not update the length accordingly.
* [Revision #34d62c7](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/34d62c7)\
  2016-01-10 23:04:34 +0100
  * Fix and testcase for the Bug [ODBC-26](https://jira.mariadb.org/browse/ODBC-26) The patch fixes various problems around DAE functionality, and in particular with WCHAR type at DAE
* [Revision #d5130e7](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/d5130e7)\
  2015-12-12 13:44:09 +0100
  * Fix of the build problem in the VS 2015. Fix of some compilation warnings in VS2015
* [Revision #96e7aeb](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/96e7aeb)\
  2015-12-10 19:17:29 +0100
  * Fixed 2 tests in the types suite - they could fail in case of specific connection charsets. Added to the framework functions to facilitate obtaining of additional connection by tests.
* [Revision #bbe3c2c](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/bbe3c2c)\
  2015-12-08 16:49:22 +0100
  * Some minor changes done while merged 2.0 to the main branch Types/typos corrections, casts etc. Several of tests in catalog have been corrected
* [Revision #98a0e8d](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/98a0e8d)\
  2015-11-19 00:26:40 +0100
  * Fixed possible crash - in some conditions TypeName in the ird record could freed, but never allocated before
* [Revision #182673d](https://github.com/mariadb-corporation/mariadb-connector-odbc/commit/182673d)\
  2015-11-17 17:22:42 +0200
  * Version bump -> 2.0.10

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
