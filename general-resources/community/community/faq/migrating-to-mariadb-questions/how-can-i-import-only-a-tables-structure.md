# How can I Import Only a Table's Structure?

The easiest way to import only the structure of databases and tables is to export only that, and not the data. You can use [mysqldump](https://github.com/mariadb-corporation/docs-server/blob/test/clients-and-utilities/legacy-clients-and-utilities/mysqldump.md) to export your database with `--no-data` option. Many GUI clients have similar options. Importing schema from other database systems, though, is more difficult and may not be possible.

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
