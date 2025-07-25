# Connector/Node.js 3.4.0 Release Notes

{% include "../../../.gitbook/includes/latest-nodejs.md" %}

[Download](https://mariadb.com/downloads/connectors/connectors-data-access/nodejs-connector) | [Release Notes](mariadb-connector-node-js-3-4-0-release-notes.md) | [Changelog](../changelogs/mariadb-connector-nodejs-3x-changelogs/mariadb-connector-node-js-3-4-0-changelog.md) | [Connector/Node.js Overview](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-nodejs/mariadb-connector-node-js-guide)

**Release date:** 24 Oct 2024

MariaDB Connector/Node.js 3.4.0 is a [_**Stable**_](../../../community-server/about/release-criteria.md) _**(GA)**_ release.

{% hint style="success" %}
**For an overview of MariaDB Connector/Node.js see the** [**About MariaDB Connector/Node.js**](https://app.gitbook.com/s/CjGYMsT2MVP4nd3IyW2L/mariadb-connector-nodejs/mariadb-connector-node-js-guide) **page**
{% endhint %}

## Notable changes

* [CONJS-299](https://jira.mariadb.org/browse/CONJS-299) Support of the PARSEC Authentication Plugin which is provided starting with MariaDB Server 11.6. See the [PARSEC Authentication Plugin documentation](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/plugins/authentication-plugins/authentication-plugin-parsec) for more details
* [CONJS-295](https://jira.mariadb.org/browse/CONJS-295) A new option jsonStrings has been added which can be used to return a JSON field as type string instead of type JSON

When working with JSON fields in MariaDB and MySQL, it's important to note that the handling differs between the two database systems.

* autoJsonMap Option: The autoJsonMap option provides flexibility in MariaDB. You can choose to have the connector return either JSON objects or string representations of the JSON data.
* jsonStrings Option: The jsonStrings option introduces a similar choice for MySQL JSON fields. It allows you to specify whether the connector should return JSON objects or string values.

In essence, the JSON fields will be returned either as a JSON or String will depend on 2 different options depending on the database you’re working with.

* [CONJS-296](https://jira.mariadb.org/browse/CONJS-296) Add option enableKeepAlive / keepAliveInitialDelay alias for keepAliveDelay for mysql2 compatibility

The _keepAliveDelay_ option in MariaDB connectors controls the frequency of keep-alive packets sent to maintain a persistent connection.

* Disabled: When set to 0, keep-alive functionality is disabled.
* Enabled: For any non-zero value, keep-alive packets are sent at the specified interval.

MySQL 2 Compatibility:\
To ensure compatibility with the MySQL 2 connector, the _enableKeepAlive_ and _keepAliveInitialDelay_ options have been added.

* enableKeepAlive: If disabled, keepAliveDelay is automatically set to 0, effectively disabling keep-alive.
* enableKeepAlive: If enabled, keepAliveDelay is set to the value specified in keepAliveInitialDelay.

In summary, the _keepAliveDelay_ option determines the keep-alive frequency, while the _enableKeepAlive_ and _keepAliveInitialDelay_ options provide compatibility with MySQL 2 connectors by allowing you to control whether keep-alive is enabled and set the initial delay.

## Issues Fixed

[CONJS-303](https://jira.mariadb.org/browse/CONJS-303) DMLs are not returning an output while streaming

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
