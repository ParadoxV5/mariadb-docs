
# Information Schema TABLE_CONSTRAINTS Table

The [Information Schema](../README.md) `TABLE_CONSTRAINTS` table contains information about tables that have [constraints](../../../../data-definition/constraint.md).


It has the following columns:



| Column | Description |
| --- | --- |
| CONSTRAINT_CATALOG | Always def. |
| CONSTRAINT_SCHEMA | Database name containing the constraint. |
| CONSTRAINT_NAME | Constraint name. |
| TABLE_SCHEMA | Database name. |
| TABLE_NAME | Table name. |
| CONSTRAINT_TYPE | Type of constraint; one of UNIQUE, PRIMARY KEY, FOREIGN KEY or CHECK. |



The [REFERENTIAL_CONSTRAINTS](information-schema-referential_constraints-table.md) table has more information about foreign keys.


<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>


{% @marketo/form formId="4316" %}
