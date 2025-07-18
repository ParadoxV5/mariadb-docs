# MariaDB Connector/J 2.5.0 Release Notes

{% include "../../../.gitbook/includes/latest-java.md" %}

[Download](https://downloads.mariadb.com/Connectors/java/connector-java-2.5.0)[Release Notes](mariadb-connector-j-250-release-notes.md)[Changelog](../changelogs/2.5/mariadb-connector-j-250-changelog.md)[Connector/J Overview](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md)

**Release date:** 3 Oct 2019

MariaDB Connector/J 2.5.0 is a [_**Release Candidate (RC)**_](../../../mariadb-release-criteria.md) release.

**NOTE:** MariaDB Connector/J 2.5.0 is fully compatible with the latest release of\
version 2.4. Further maintenance releases will not be provided for version 2.4.

**For an overview of MariaDB Connector/J see the**[**About MariaDB Connector/J**](https://github.com/mariadb-corporation/docs-release-notes/blob/test/kb/en/about-mariadb-connector-j/README.md) **page**

## Evolutions

### Authentication service

[Client authentication plugins](https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/reference/plugins/authentication-plugins) are now defined as services. This permits to easily add new client authentication plugins.\
The driver has 2 new plugins `caching_sha2_password` and `sha256_password plugin` for MySQL compatibility

List of authentication plugins in java connector :

* mysql\_clear\_password
* auth\_gssapi\_client
* client\_ed25519
* mysql\_native\_password
* mysql\_old\_password
* dialog (PAM)
* sha256\_password
* caching\_sha2\_password

New authentication plugins can be created implementing interface org.mariadb.jdbc.authentication.AuthenticationPlugin, and listing new plugin in a META-INF/services/org.mariadb.jdbc.authentication.AuthenticationPlugin file.

### Credential service

Credentials are usually set using user/password in the connection string or by using DriverManager.getConnection(String url, String user, String password).

Credential plugins permit to provide credential information from other means. Those plugins have to be activated setting option `credentialType` to designated plugin.

The driver has 3 default plugins :

#### AWS IAM

This permits AWS database IAM authentication. The plugin generate a token using IAM credential and region. Token is valid for 15 minutes and cached for 10 minutes.

To use this credential authentication, com.amazonaws:aws-java-sdk-rds dependency must be registred in classpath.\
Implementation use SDK DefaultAWSCredentialsProviderChain and DefaultAwsRegionProviderChain to get IAM credential and region.\
see [DefaultAWSCredentialsProviderChain](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/auth/DefaultAWSCredentialsProviderChain.html) and [DefaultAwsRegionProviderChain](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/auth/DefaultAWSCredentialsProviderChain.html) to check how those information can be retrieved (environment variable / system properties, files, ...)

Example: `jdbc:mariadb://host/db?credentialType=AWS-IAM&useSsl&serverSslCert=/somepath/rds-combined-ca-bundle.pem`

with AWS\_ACCESS\_KEY\_ID, AWS\_SECRET\_ACCESS\_KEY and AWS\_REGION environment variable set.

#### Environment

User and Password are retrieved from environment variables. default environment variables are MARIADB\_USER and MARIADB\_PWD, but can be changed by setting additional option `userKey` and `pwdKey`

Example : using connection string `jdbc:mariadb://host/db?credentialType=ENV` user and password will be retrieved from environment variable MARIADB\_USER and MARIADB\_PWD.

#### Property

User and Password are retrieved from java properties. default property name are mariadb.user and mariadb.pwd, but property names can be changed by setting additional option `userKey` and `pwdKey`

Example : using connection string `jdbc:mariadb://host/db?credentialType=PROPERTY&userKey=mariadbUser&pwdKey=mariadbPwd` user and password will be retrieved from java properties `mariadbUser` and `mariadbPwd`

### SSL factory service

A connection to a server initially creates a socket. When set, SSL socket is layered over this existing socket.\
Implementing org.mariadb.jdbc.tls.TlsSocketPlugin permit to provide custom SSL implementation for example create a new [HostnameVerifier](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/net/ssl/HostnameVerifier.html) implementation.

Custom implementation need to implement org.mariadb.jdbc.tls.TlsSocketPlugin and register service META-INF/services/org.mariadb.jdbc.tls.TlsSocketPlugin

Custom implementation are activated using option `tlsSocketType`

## Other

* [CONJ-561](https://jira.mariadb.org/browse/CONJ-561) : JDBC 4.3 partial implementation java.sql.Statement methods isSimpleIdentifier, enquoteIdentifier,\
  enquoteLiteral and enquoteNCharLiteral
* [CONJ-692](https://jira.mariadb.org/browse/CONJ-692) : ConnectionPoolDataSource interface addition to MariaDbPoolDataSource
* [CONJ-563](https://jira.mariadb.org/browse/CONJ-563) : closing possible option batch thread on driver deregistration.

## Bug fixes

* [CONJ-732](https://jira.mariadb.org/browse/CONJ-732) : Driver getPropertyInfo returns no options information when url is empty
* [CONJ-734](https://jira.mariadb.org/browse/CONJ-734) : DatabaseMetaData.getSchemaTerm now return "schema", not empty string

## New options

| credentialType          | tlsSocketType                                                                                                  | serverRsaPublicKeyFile | allowPublicKeyRetrieval |
| ----------------------- | -------------------------------------------------------------------------------------------------------------- | ---------------------- | ----------------------- |
| credentialType          | Indicate the credential plugin type to use. Plugin must be present in classpath                                |                        |                         |
| tlsSocketType           | Indicate TLS socket type implementation                                                                        |                        |                         |
| serverRsaPublicKeyFile  | Indicate path to MySQL server public RSA key file                                                              |                        |                         |
| allowPublicKeyRetrieval | Authorize client to ask MySQL server public RSA key file if not set using serverRsaPublicKeyFileDefault: false |                        |                         |

## Changelog

For a complete list of changes made in MariaDB Connector/J 2.5.0, with links to detailed\
information on each push, see the [changelog](../changelogs/2.5/mariadb-connector-j-250-changelog.md).

{% include "https://app.gitbook.com/s/SsmexDFPv2xG2OTyO5yV/~/reusable/pNHZQXPP5OEz2TgvhFva/" %}

{% @marketo/form formid="4316" formId="4316" %}
