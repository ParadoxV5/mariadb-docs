# Release Notes for MariaDB Enterprise Server 10.5.19-14

MariaDB Enterprise Server 10.5.19-14 has been withdrawn, and is no longer available from MariaDB package repositories.

A regression has been reported for MariaDB Enterprise Server 10.5.19-14, which results in InnoDB not freeing undo logs when they are no longer needed. This issue could cause the InnoDB system tablespace or the undo log tablespaces to grow indefinitely.

Customers who have deployed MariaDB Enterprise Server 10.5.19-14 may contact MariaDB Support for assistance or upgrade to the next maintenance release. The next maintenance release of MariaDB Enterprise Server is scheduled for 2023-06-12.

<sub>_This page is: Copyright © 2025 MariaDB. All rights reserved._</sub>

{% @marketo/form formid="4316" formId="4316" %}
