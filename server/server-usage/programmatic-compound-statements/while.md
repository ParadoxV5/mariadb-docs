# WHILE

## Syntax

```
[begin_label:] WHILE search_condition DO
    statement_list
END WHILE [end_label]
```

## Description

The statement list within a `WHILE` statement is repeated as long as the`search_condition` is true. statement\_list consists of one or more\
statements. If the loop must be executed at least once, [REPEAT ... LOOP](repeat-loop.md) can be used instead.

A `WHILE` statement can be [labeled](labels.md). end\_label cannot be given unless\
begin\_label also is present. If both are present, they must be the\
same.

## Examples

```
CREATE PROCEDURE dowhile()
BEGIN
  DECLARE v1 INT DEFAULT 5;

  WHILE v1 > 0 DO
    ...
    SET v1 = v1 - 1;
  END WHILE;
END
```

<sub>_This page is licensed: GPLv2, originally from [fill\_help\_tables.sql](https://github.com/MariaDB/server/blob/main/scripts/fill_help_tables.sql)_</sub>

{% @marketo/form formId="4316" %}
