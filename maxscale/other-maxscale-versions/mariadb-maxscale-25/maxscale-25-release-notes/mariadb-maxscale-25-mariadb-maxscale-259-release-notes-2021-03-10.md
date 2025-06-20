# MariaDB MaxScale 2.5.9 Release Notes -- 2021-03-10

Release 2.5.9 is a GA release.

This document describes the changes in release 2.5.9, when compared to the\
previous release in the same series.

If you are upgrading from an older major version of MaxScale, please read the[upgrading document](../maxscale-25-upgrading/mariadb-maxscale-25-upgrading-mariadb-maxscale-from-24-to-25.md) for\
this MaxScale version.

For any problems you encounter, please consider submitting a bug\
report on [our Jira](https://jira.mariadb.org/projects/MXS).

### Bug fixes

* [MXS-3428](https://jira.mariadb.org/browse/MXS-3428) Regression in max\_slave\_replication\_lag
* [MXS-3426](https://jira.mariadb.org/browse/MXS-3426) MaxScale with SSL in Azure Cloud not working properly
* [MXS-3419](https://jira.mariadb.org/browse/MXS-3419) Token authentication doesn't perform authorization
* [MXS-3416](https://jira.mariadb.org/browse/MXS-3416) causal\_reads=global returns an unexpected OK packet
* [MXS-3409](https://jira.mariadb.org/browse/MXS-3409) Need more GRANTs to be documented for connecting to xpand direct using xpandmon
* [MXS-3404](https://jira.mariadb.org/browse/MXS-3404) maxscale write in the slave with function
* [MXS-3392](https://jira.mariadb.org/browse/MXS-3392) Reset implementation on failing prepared statement

### Known Issues and Limitations

There are some limitations and known issues within this version of MaxScale.\
For more information, please refer to the [Limitations](../about-maxscale-25/mariadb-maxscale-25-limitations-and-known-issues-within-mariadb-maxscale.md) document.

### Packaging

RPM and Debian packages are provided for supported the Linux distributions.

Packages can be downloaded [here](https://mariadb.com/downloads/#mariadb_platform-mariadb_maxscale).

### Source Code

The source code of MaxScale is tagged at GitHub with a tag, which is identical\
with the version of MaxScale. For instance, the tag of version X.Y.Z of MaxScale\
is `maxscale-X.Y.Z`. Further, the default branch is always the latest GA version\
of MaxScale.

The source code is available [here](https://github.com/mariadb-corporation/MaxScale).

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
