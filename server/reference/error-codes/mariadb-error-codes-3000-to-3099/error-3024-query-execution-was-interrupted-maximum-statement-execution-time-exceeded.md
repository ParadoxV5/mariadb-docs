# Error 3024: Query execution was interrupted, maximum statement execution time exceeded

| Error Code | SQLSTATE | Error              | Description                                                                |
| ---------- | -------- | ------------------ | -------------------------------------------------------------------------- |
| 3024       |          | ER\_QUERY\_TIMEOUT | Query execution was interrupted, maximum statement execution time exceeded |

## Possible Causes and Solutions

The cause is that the executing statement took more than [max\_statement\_time](../../../ha-and-performance/optimization-and-tuning/system-variables/server-system-variables.md#max_statement_time) (primary) or [slave\_max\_statement\_time](../../../ha-and-performance/standard-replication/replication-and-binary-log-system-variables.md#slave_max_statement_time) (replica) to execute.

To fix this, you have to either increase the value of [max\_statement\_time](../../../ha-and-performance/optimization-and-tuning/system-variables/server-system-variables.md#max_statement_time) or find out [why the query is slow](../../../ha-and-performance/optimization-and-tuning/query-optimizations/). Start by doing an [EXPLAIN](../../sql-statements/administrative-sql-statements/analyze-and-explain-statements/explain.md) or [ANALYZE](../../sql-statements/administrative-sql-statements/analyze-and-explain-statements/analyze-statement.md) on the query to find out how the query is executed.

## See Also

* [Aborting Statements that Exceed a Certain Time to Execute](../../../ha-and-performance/optimization-and-tuning/query-optimizations/aborting-statements.md)

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
