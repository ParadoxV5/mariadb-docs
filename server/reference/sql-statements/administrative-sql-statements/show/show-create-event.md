# SHOW CREATE EVENT

## Syntax

```
SHOW CREATE EVENT event_name
```

## Description

This statement displays the [CREATE EVENT](../../data-definition/create/create-event.md) statement that creates a given [event](../../../../server-usage/triggers-events/event-scheduler/events.md), as well as the [SQL\_MODE](../../../../server-management/variables-and-modes/sql-mode.md) that was used when the trigger has been created and the character set used by the connection. To find out which events are present, use [SHOW EVENTS](show-events.md).

`SHOW CREATE EVENT` quotes identifiers according to the value of the [sql\_quote\_show\_create](../../../../ha-and-performance/optimization-and-tuning/system-variables/server-system-variables.md#sql_quote_show_create) system variable. Prior to [MariaDB 10.6.5](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/mariadb-10-6-series/mariadb-1065-release-notes), [MariaDB 10.5.13](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/mariadb-10-5-series/mariadb-10513-release-notes) and [MariaDB 10.4.22](https://app.gitbook.com/s/aEnK0ZXmUbJzqQrTjFyb/mariadb-community-server-release-notes/old-releases/release-notes-mariadb-10-4-series/mariadb-10422-release-notes), the output of this statement was unreliably affected by the [sql\_quote\_show\_create](../../../../ha-and-performance/optimization-and-tuning/system-variables/server-system-variables.md#sql_quote_show_create) system variable.

The [information\_schema.EVENTS](../system-tables/information-schema/information-schema-tables/information-schema-events-table.md) table provides similar, but more complete, information.

## Examples

```
SHOW CREATE EVENT test.e_daily\G
*************************** 1. row ***************************
               Event: e_daily
            sql_mode: 
           time_zone: SYSTEM
        Create Event: CREATE EVENT `e_daily`
                        ON SCHEDULE EVERY 1 DAY
                        STARTS CURRENT_TIMESTAMP + INTERVAL 6 HOUR
                        ON COMPLETION NOT PRESERVE
                        ENABLE
                        COMMENT 'Saves total number of sessions then
                                clears the table each day'
                        DO BEGIN
                          INSERT INTO site_activity.totals (time, total)
                            SELECT CURRENT_TIMESTAMP, COUNT(*) 
                            FROM site_activity.sessions;
                          DELETE FROM site_activity.sessions;
                        END
character_set_client: latin1
collation_connection: latin1_swedish_ci
  Database Collation: latin1_swedish_ci
```

## See also

* [Events Overview](../../../../server-usage/triggers-events/event-scheduler/events.md)
* [CREATE EVENT](../../data-definition/create/create-event.md)
* [ALTER EVENT](../../../../server-usage/triggers-events/event-scheduler/alter-event.md)
* [DROP EVENT](../../data-definition/drop/drop-event.md)

<sub>_This page is licensed: GPLv2, originally from [fill\_help\_tables.sql](https://github.com/MariaDB/server/blob/main/scripts/fill_help_tables.sql)_</sub>

{% @marketo/form formId="4316" %}
