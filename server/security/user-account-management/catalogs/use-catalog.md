# USE CATALOG

**MariaDB starting with** [**12.0**](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/community-server/release-notes-mariadb-12.0-rolling-releases/what-is-mariadb-120)

Catalog support is planned for 12.0.

## Syntax

```bnf
USE CATALOG catalog_name
```

## Description

Changes to another [catalog](./).\
Can only be done by a super user in the 'def' catalog.\
Changing catalog will update catalog status and reset all session status.

A tenant (a user in any other catalog than 'def') cannot change to another catalog.\
However tenants can execute `USE CATALOG current_catalog`. This is to allow the\
user to import SQL scripts that use `USE CATALOG...`.

## See Also

* [USE database](../../../reference/sql-statements/administrative-sql-statements/use-database.md). Changing database.

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
