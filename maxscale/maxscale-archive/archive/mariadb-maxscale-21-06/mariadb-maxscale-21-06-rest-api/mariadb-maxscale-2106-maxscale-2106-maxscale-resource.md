# MaxScale 21.06 MaxScale Resource

The MaxScale resource represents a MaxScale instance and it is the core on top\
of which the modules build upon.

* [MaxScale Resource](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#maxscale-resource)
  * [Resource Operations](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#resource-operations)
  * [Get global information](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-global-information)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response)
  * [Update MaxScale parameters](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#update-maxscale-parameters)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_1)
  * [Get thread information](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-thread-information)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_2)
  * [Get information for all threads](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-information-for-all-threads)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_3)
  * [Get logging information](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-logging-information)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_4)
  * [Get log data](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-log-data)
    * [Parameters](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#parameters)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_5)
  * [Stream log data](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#stream-log-data)
    * [Limitations](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#limitations)
      * [Parameters](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#parameters_1)
      * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_6)
  * [Update logging parameters](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#update-logging-parameters)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_7)
  * [Flush and rotate log files](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#flush-and-rotate-log-files)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_8)
  * [Get task schedule](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-task-schedule)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_9)
  * [Get a loaded module](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-a-loaded-module)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_10)
  * [Get all loaded modules](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#get-all-loaded-modules)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_11)
  * [Call a module command](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#call-a-module-command)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_12)
  * [Classify a statement](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#classify-a-statement)
    * [Response](mariadb-maxscale-2106-maxscale-2106-maxscale-resource.md#response_13)

### Resource Operations

### Get global information

```
GET /v1/maxscale
```

Retrieve global information about a MaxScale instance. This includes various\
file locations, configuration options and version information.

**Response**

`Status: 200 OK`

```
{
    "data": {
        "attributes": {
            "activated_at": "Thu, 20 Jul 2023 15:20:06 GMT",
            "commit": "1dd63c813dccada2dba65e62bfd7faebccaa1bc9",
            "config_sync": null,
            "parameters": {
                "admin_auth": true,
                "admin_enabled": true,
                "admin_gui": true,
                "admin_host": "127.0.0.1",
                "admin_log_auth_failures": true,
                "admin_pam_readonly_service": null,
                "admin_pam_readwrite_service": null,
                "admin_port": 8989,
                "admin_secure_gui": true,
                "admin_ssl_ca_cert": null,
                "admin_ssl_cert": null,
                "admin_ssl_key": null,
                "admin_ssl_version": "MAX",
                "auth_connect_timeout": "10000ms",
                "auth_read_timeout": "10000ms",
                "auth_write_timeout": "10000ms",
                "cachedir": "/var/cache/maxscale",
                "config_sync_cluster": null,
                "config_sync_db": "mysql",
                "config_sync_interval": "5000ms",
                "config_sync_password": null,
                "config_sync_timeout": "10000ms",
                "config_sync_user": null,
                "connector_plugindir": "/usr/lib64/maxscale/plugin",
                "datadir": "/var/lib/maxscale",
                "debug": null,
                "dump_last_statements": "never",
                "execdir": "/usr/bin",
                "language": "/var/lib/maxscale",
                "libdir": "/usr/lib64/maxscale",
                "load_persisted_configs": true,
                "local_address": null,
                "log_debug": false,
                "log_info": false,
                "log_notice": true,
                "log_throttling": {
                    "count": 10,
                    "suppress": 10000,
                    "window": 1000
                },
                "log_warn_super_user": false,
                "log_warning": true,
                "logdir": "/var/log/maxscale",
                "max_auth_errors_until_block": 10,
                "maxlog": true,
                "module_configdir": "/etc/maxscale.modules.d",
                "ms_timestamp": false,
                "passive": false,
                "persistdir": "/var/lib/maxscale/maxscale.cnf.d",
                "piddir": "/var/run/maxscale",
                "query_classifier": "qc_sqlite",
                "query_classifier_args": null,
                "query_classifier_cache_size": 5003807539,
                "query_retries": 1,
                "query_retry_timeout": "5000ms",
                "rebalance_period": "0ms",
                "rebalance_threshold": 20,
                "rebalance_window": 10,
                "retain_last_statements": 0,
                "session_trace": 0,
                "skip_name_resolve": false,
                "skip_permission_checks": false,
                "sql_mode": "default",
                "syslog": false,
                "threads": 8,
                "users_refresh_interval": "0ms",
                "users_refresh_time": "30000ms",
                "writeq_high_water": 16777216,
                "writeq_low_water": 8192
            },
            "process_datadir": "/var/lib/maxscale/data19",
            "started_at": "Thu, 20 Jul 2023 15:20:06 GMT",
            "uptime": 10,
            "version": "6.4.7"
        },
        "id": "maxscale",
        "type": "maxscale"
    },
    "links": {
        "self": "http://localhost:8989/v1/maxscale/"
    }
}
```

### Update MaxScale parameters

```
PATCH /v1/maxscale
```

Update MaxScale parameters. The request body must define updated values for the`data.attributes.parameters` object. The parameters that can be modified are\
listed in the `/v1/maxscale/modules/maxscale` endpoint and have the `modifiable`\
value set to `true`.

**Response**

Parameters modified:

`Status: 204 No Content`

Invalid JSON body:

`Status: 403 Forbidden`

### Get thread information

```
GET /v1/maxscale/threads/:id
```

Get the information and statistics of a particular thread. The _:id_ in\
the URI must map to a valid thread number between 0 and the configured\
value of `threads`.

**Response**

`Status: 200 OK`

```
{
    "data": {
        "attributes": {
            "stats": {
                "accepts": 1,
                "avg_event_queue_length": 1,
                "current_descriptors": 7,
                "errors": 0,
                "hangups": 0,
                "load": {
                    "last_hour": 0,
                    "last_minute": 0,
                    "last_second": 0
                },
                "max_event_queue_length": 2,
                "max_exec_time": 0,
                "max_queue_time": 0,
                "query_classifier_cache": {
                    "evictions": 0,
                    "hits": 0,
                    "inserts": 1,
                    "misses": 2,
                    "size": 368
                },
                "reads": 36,
                "total_descriptors": 7,
                "writes": 13
            }
        },
        "id": "0",
        "links": {
            "self": "http://localhost:8989/v1/threads/0/"
        },
        "type": "threads"
    },
    "links": {
        "self": "http://localhost:8989/v1/maxscale/threads/0/"
    }
}
```

### Get information for all threads

```
GET /v1/maxscale/threads
```

Get the information for all threads. Returns a collection of threads resources.

**Response**

`Status: 200 OK`

```
{
    "data": [
        {
            "attributes": {
                "stats": {
                    "accepts": 1,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 7,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 2,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 1,
                        "misses": 2,
                        "size": 368
                    },
                    "reads": 37,
                    "total_descriptors": 7,
                    "writes": 13
                }
            },
            "id": "0",
            "links": {
                "self": "http://localhost:8989/v1/threads/0/"
            },
            "type": "threads"
        },
        {
            "attributes": {
                "stats": {
                    "accepts": 0,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 4,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 1,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 0,
                        "misses": 0,
                        "size": 0
                    },
                    "reads": 26,
                    "total_descriptors": 4,
                    "writes": 0
                }
            },
            "id": "1",
            "links": {
                "self": "http://localhost:8989/v1/threads/1/"
            },
            "type": "threads"
        },
        {
            "attributes": {
                "stats": {
                    "accepts": 0,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 4,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 1,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 0,
                        "misses": 0,
                        "size": 0
                    },
                    "reads": 24,
                    "total_descriptors": 4,
                    "writes": 0
                }
            },
            "id": "2",
            "links": {
                "self": "http://localhost:8989/v1/threads/2/"
            },
            "type": "threads"
        },
        {
            "attributes": {
                "stats": {
                    "accepts": 0,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 4,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 1,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 0,
                        "misses": 0,
                        "size": 0
                    },
                    "reads": 24,
                    "total_descriptors": 4,
                    "writes": 0
                }
            },
            "id": "3",
            "links": {
                "self": "http://localhost:8989/v1/threads/3/"
            },
            "type": "threads"
        },
        {
            "attributes": {
                "stats": {
                    "accepts": 0,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 4,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 1,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 0,
                        "misses": 0,
                        "size": 0
                    },
                    "reads": 24,
                    "total_descriptors": 4,
                    "writes": 0
                }
            },
            "id": "4",
            "links": {
                "self": "http://localhost:8989/v1/threads/4/"
            },
            "type": "threads"
        },
        {
            "attributes": {
                "stats": {
                    "accepts": 0,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 4,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 1,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 0,
                        "misses": 0,
                        "size": 0
                    },
                    "reads": 25,
                    "total_descriptors": 4,
                    "writes": 0
                }
            },
            "id": "5",
            "links": {
                "self": "http://localhost:8989/v1/threads/5/"
            },
            "type": "threads"
        },
        {
            "attributes": {
                "stats": {
                    "accepts": 0,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 4,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 1,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 0,
                        "misses": 0,
                        "size": 0
                    },
                    "reads": 25,
                    "total_descriptors": 4,
                    "writes": 0
                }
            },
            "id": "6",
            "links": {
                "self": "http://localhost:8989/v1/threads/6/"
            },
            "type": "threads"
        },
        {
            "attributes": {
                "stats": {
                    "accepts": 0,
                    "avg_event_queue_length": 1,
                    "current_descriptors": 4,
                    "errors": 0,
                    "hangups": 0,
                    "load": {
                        "last_hour": 0,
                        "last_minute": 0,
                        "last_second": 0
                    },
                    "max_event_queue_length": 1,
                    "max_exec_time": 0,
                    "max_queue_time": 0,
                    "query_classifier_cache": {
                        "evictions": 0,
                        "hits": 0,
                        "inserts": 0,
                        "misses": 0,
                        "size": 0
                    },
                    "reads": 25,
                    "total_descriptors": 4,
                    "writes": 0
                }
            },
            "id": "7",
            "links": {
                "self": "http://localhost:8989/v1/threads/7/"
            },
            "type": "threads"
        }
    ],
    "links": {
        "self": "http://localhost:8989/v1/maxscale/threads/"
    }
}
```

### Get logging information

```
GET /v1/maxscale/logs
```

Get information about the current state of logging, enabled log files and the\
location where the log files are stored.

**Note:** The parameters in this endpoint are a subset of the parameters in the`/v1/maxscale` endpoint. Because of this, the parameters in this endpoint are\
deprecated as of MaxScale 6.0.

**Note:** In MaxScale 2.5 the `log_throttling` and `ms_timestamp` parameters\
were incorrectly named as `throttling` and `highprecision`. In MaxScale 6,\
the parameter names are now correct which means the parameters declared here\
aren't fully backwards compatible.

**Response**

`Status: 200 OK`

```
{
    "data": {
        "attributes": {
            "log_file": "/var/log/maxscale/maxscale.log",
            "log_priorities": [
                "alert",
                "error",
                "warning",
                "notice"
            ],
            "parameters": {
                "log_debug": false,
                "log_info": false,
                "log_notice": true,
                "log_throttling": {
                    "count": 10,
                    "suppress": 10000,
                    "window": 1000
                },
                "log_warning": true,
                "maxlog": true,
                "ms_timestamp": false,
                "syslog": false
            }
        },
        "id": "logs",
        "type": "logs"
    },
    "links": {
        "self": "http://localhost:8989/v1/maxscale/logs/"
    }
}
```

### Get log data

```
GET /v1/maxscale/logs/data
```

Get the contents of the MaxScale logs. This endpoint was added in MaxScale 6.

To navigate the log, use the `prev` link to move backwards to older log\
entries. The latest log entries can be read with the `last` link.

The entries are sorted in ascending order by the time they were logged. This\
means that with the default parameters, the latest logged event is the last\
element in the returned array.

**Parameters**

This endpoint supports the following parameters:

* `page[size]`
* Set number of rows of data to read. By default, 50 rows of data are read\
  from the log.
* `page[cursor]`
* Set position from where the log data is retrieved. The default position to\
  retrieve the log data is the end of the log.\
  This value should not be modified by the user and the values returned in the`links` object should be used instead. This way the navigation will provide\
  a consistent view of the log that does not overlap.\
  Optionally, the `id` values in the returned data can be used as the values\
  for this parameter to read data from a known point in the file.
* `priority`
* Include messages only from these log levels. The default is to include all\
  messages.\
  The value given should be a comma-separated list of log priorities. The\
  priorities are `alert`, `error`, `warning`, `notice`, `info` and`debug`. Note that the `debug` log level is only used in debug builds of\
  MaxScale.

**Response**

`Status: 200 OK`

```
{
    "data": {
        "attributes": {
            "log": [
                {
                    "id": "42",
                    "message": "Service 'RW-Split-Router' started (2/2)",
                    "priority": "notice",
                    "timestamp": "2023-07-20 15:20:06"
                },
                {
                    "id": "43",
                    "message": "Read 5 user@host entries from 'server1' for service 'RW-Split-Router'.",
                    "priority": "notice",
                    "timestamp": "2023-07-20 15:20:07"
                },
                {
                    "id": "44",
                    "message": "Read 5 user@host entries from 'server1' for service 'Read-Connection-Router'.",
                    "priority": "notice",
                    "timestamp": "2023-07-20 15:20:07"
                }
            ],
            "log_source": "maxlog"
        },
        "id": "log_data",
        "type": "log_data"
    },
    "links": {
        "last": "http://localhost:8989/v1/maxscale/logs/data/?page%5Bsize%5D=3",
        "prev": "http://localhost:8989/v1/maxscale/logs/data/?page%5Bcursor%5D=39&page%5Bsize%5D=3",
        "self": "http://localhost:8989/v1/maxscale/logs/data/?page%5Bcursor%5D=42&page%5Bsize%5D=3"
    }
}
```

### Stream log data

```
GET /v1/maxscale/logs/stream
```

Stream the contents of the MaxScale logs. This endpoint was added in MaxScale 6.

This endpoint opens a [WebSocket](https://tools.ietf.org/html/rfc6455)\
connection and streams the contents of the log to it. Each WebSocket message\
will contain the JSON representation of the log message. The JSON is formatted\
in the same way as the values in the `log` array of the `/v1/maxscale/logs/data`\
endpoint:

```
{
    "id": "572",
    "message": "MaxScale started with 8 worker threads, each with a stack size of 8388608 bytes.",
    "priority": "notice",
    "timestamp": "2020-09-25 10:01:29"
}
```

#### Limitations

* If the client writes any data to the open socket, it will be treated as\
  an error and the stream is closed.
* The WebSocket ping and close commands are not yet supported and will be\
  treated as errors.
* When `maxlog` is used as source of log data, any log messages logged after log\
  rotation will not be sent if the file was moved or truncated. To fetch new\
  events after log rotation, reopen the WebSocket connection.

**Parameters**

This endpoint supports the following parameters:

* `page[cursor]`
* Set position from where the log data is retrieved. The default position to\
  retrieve the log data is the end of the log.\
  To stream data from a known point, first read the data via the`/v1/maxscale/logs/data` endpoint and then use the `id` value of the newest\
  log message (i.e. the first value in the `log` array) to start the stream.
* `priority`
* Include messages only from these log levels. The default is to include all\
  messages.\
  The value given should be a comma-separated list of log priorities. The\
  priorities are `alert`, `error`, `warning`, `notice`, `info` and`debug`. Note that the `debug` log level is only used in debug builds of\
  MaxScale.

**Response**

Upgrade started:

`Status: 101 Switching Protocols`

Client didn't request a WebSocket upgrade:

`Status: 426 Upgrade Required`

### Update logging parameters

**Note:** The modification of logging parameters via this endpoint has\
deprecated in MaxScale 6.0. The parameters should be modified with the`/v1/maxscale` endpoint instead.

Any PATCH requests done to this endpoint will be redirected to the`/v1/maxscale` endpoint. Due to the mispelling of the `ms_timestamp` and`log_throttling` parameters, this is not fully backwards compatible.

```
PATCH /v1/maxscale/logs
```

Update logging parameters. The request body must define updated values for the`data.attributes.parameters` object. All logging parameters can be altered at runtime.

**Response**

Parameters modified:

`Status: 204 No Content`

Invalid JSON body:

`Status: 403 Forbidden`

### Flush and rotate log files

```
POST /v1/maxscale/logs/flush
```

Flushes any pending messages to disk and reopens the log files. The body of the\
message is ignored.

**Response**

`Status: 204 No Content`

### Get task schedule

```
GET /v1/maxscale/tasks
```

Retrieve all pending tasks that are queued for execution.

**Response**

`Status: 200 OK`

```
{
    "links": {
        "self": "http://localhost:8989/v1/maxscale/tasks/"
    },
    "data": [] // No tasks active
}
```

### Get a loaded module

```
GET /v1/maxscale/modules/:name
```

Retrieve information about a loaded module. The _:name_ must be the name of a\
valid loaded module or either `maxscale` or `servers`.

The `maxscale` module will display the global configuration options\
(i.e. everything under the `[maxscale]` section) as a module.

The `servers` module displays the server object type and the configuration\
parameters it accepts as a module.

Any parameter with the `modifiable` value set to `true` can be modified\
at runtime using a PATCH command on the corresponding object endpoint.

**Response**

`Status: 200 OK`

```
{
    "data": {
        "attributes": {
            "api": "router",
            "commands": [],
            "description": "A Read/Write splitting router for enhancement read scalability",
            "maturity": "GA",
            "module_type": "Router",
            "parameters": [
                {
                    "default_value": "false",
                    "description": "Causal reads mode",
                    "enum_values": [
                        "false",
                        "off",
                        "0",
                        "true",
                        "on",
                        "1",
                        "none",
                        "local",
                        "global",
                        "fast"
                    ],
                    "mandatory": false,
                    "modifiable": true,
                    "name": "causal_reads",
                    "type": "enum"
                },
                {
                    "default_value": "10000ms",
                    "description": "Timeout for the slave synchronization",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "causal_reads_timeout",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": false,
                    "description": "Retry failed writes outside of transactions",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "delayed_retry",
                    "type": "bool"
                },
                {
                    "default_value": "10000ms",
                    "description": "Timeout for delayed_retry",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "delayed_retry_timeout",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": false,
                    "description": "Create connections only when needed",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "lazy_connect",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Use master for reads",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "master_accept_reads",
                    "type": "bool"
                },
                {
                    "default_value": "fail_instantly",
                    "description": "Master failure mode behavior",
                    "enum_values": [
                        "fail_instantly",
                        "fail_on_write",
                        "error_on_write"
                    ],
                    "mandatory": false,
                    "modifiable": true,
                    "name": "master_failure_mode",
                    "type": "enum"
                },
                {
                    "default_value": false,
                    "description": "Reconnect to master",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "master_reconnection",
                    "type": "bool"
                },
                {
                    "default_value": 255,
                    "description": "Maximum number of slave connections",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "max_slave_connections",
                    "type": "count"
                },
                {
                    "default_value": "0ms",
                    "description": "Maximum allowed slave replication lag",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "max_slave_replication_lag",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": false,
                    "description": "Optimistically offload transactions to slaves",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "optimistic_trx",
                    "type": "bool"
                },
                {
                    "default_value": true,
                    "description": "Automatically retry failed reads outside of transactions",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "retry_failed_reads",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Reuse identical prepared statements inside the same connection",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "reuse_prepared_statements",
                    "type": "bool"
                },
                {
                    "default_value": 255,
                    "description": "Starting number of slave connections",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "slave_connections",
                    "type": "count"
                },
                {
                    "default_value": "LEAST_CURRENT_OPERATIONS",
                    "description": "Slave selection criteria",
                    "enum_values": [
                        "LEAST_GLOBAL_CONNECTIONS",
                        "LEAST_ROUTER_CONNECTIONS",
                        "LEAST_BEHIND_MASTER",
                        "LEAST_CURRENT_OPERATIONS",
                        "ADAPTIVE_ROUTING"
                    ],
                    "mandatory": false,
                    "modifiable": true,
                    "name": "slave_selection_criteria",
                    "type": "enum"
                },
                {
                    "default_value": false,
                    "description": "Lock connection to master after multi-statement query",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "strict_multi_stmt",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Lock connection to master after a stored procedure is executed",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "strict_sp_calls",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Retry failed transactions",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "transaction_replay",
                    "type": "bool"
                },
                {
                    "default_value": 5,
                    "description": "Maximum number of times to retry a transaction",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "transaction_replay_attempts",
                    "type": "count"
                },
                {
                    "default_value": "full",
                    "description": "Type of checksum to calculate for results",
                    "enum_values": [
                        "full",
                        "result_only",
                        "no_insert_id"
                    ],
                    "mandatory": false,
                    "modifiable": true,
                    "name": "transaction_replay_checksum",
                    "type": "enum"
                },
                {
                    "default_value": 1048576,
                    "description": "Maximum size of transaction to retry",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "transaction_replay_max_size",
                    "type": "size"
                },
                {
                    "default_value": false,
                    "description": "Retry transaction on deadlock",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "transaction_replay_retry_on_deadlock",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Retry transaction on checksum mismatch",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "transaction_replay_retry_on_mismatch",
                    "type": "bool"
                },
                {
                    "default_value": "0ms",
                    "description": "Timeout for transaction replay",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "transaction_replay_timeout",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": "all",
                    "description": "Whether to route SQL variable modifications to all servers or only to the master",
                    "enum_values": [
                        "all",
                        "master"
                    ],
                    "mandatory": false,
                    "modifiable": true,
                    "name": "use_sql_variables_in",
                    "type": "enum"
                },
                {
                    "default_value": false,
                    "description": "Retrieve users from all backend servers instead of only one",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "auth_all_servers",
                    "type": "bool"
                },
                {
                    "default_value": "300000ms",
                    "description": "How ofted idle connections are pinged",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "connection_keepalive",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": "0ms",
                    "description": "Connection idle timeout",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "connection_timeout",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": false,
                    "description": "Disable session command history",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "disable_sescmd_history",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Allow the root user to connect to this service",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "enable_root_user",
                    "type": "bool"
                },
                {
                    "default_value": "-1ms",
                    "description": "Put connections into pool after session has been idle for this long",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "idle_session_pool_time",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": true,
                    "description": "Match localhost to wildcard host",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "localhost_match_wildcard_host",
                    "type": "bool"
                },
                {
                    "default_value": true,
                    "description": "Log a warning when client authentication fails",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "log_auth_warnings",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Log debug messages for this service (debug builds only)",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "log_debug",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Log info messages for this service",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "log_info",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Log notice messages for this service",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "log_notice",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Log warning messages for this service",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "log_warning",
                    "type": "bool"
                },
                {
                    "default_value": 0,
                    "description": "Maximum number of connections",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "max_connections",
                    "type": "count"
                },
                {
                    "default_value": 50,
                    "description": "Session command history size",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "max_sescmd_history",
                    "type": "count"
                },
                {
                    "default_value": "60000ms",
                    "description": "How long a session can wait for a connection to become available",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "multiplex_timeout",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "default_value": "0ms",
                    "description": "Network write timeout",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "net_write_timeout",
                    "type": "duration",
                    "unit": "ms"
                },
                {
                    "description": "Password for the user used to retrieve database users",
                    "mandatory": true,
                    "modifiable": true,
                    "name": "password",
                    "type": "string"
                },
                {
                    "default_value": true,
                    "description": "Prune old session command history if the limit is exceeded",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "prune_sescmd_history",
                    "type": "bool"
                },
                {
                    "default_value": "primary",
                    "description": "Service rank",
                    "enum_values": [
                        "primary",
                        "secondary"
                    ],
                    "mandatory": false,
                    "modifiable": true,
                    "name": "rank",
                    "type": "enum"
                },
                {
                    "default_value": -1,
                    "description": "Number of statements kept in memory",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "retain_last_statements",
                    "type": "int"
                },
                {
                    "default_value": false,
                    "description": "Enable session tracing for this service",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "session_trace",
                    "type": "bool"
                },
                {
                    "default_value": false,
                    "description": "Track session state using server responses",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "session_track_trx_state",
                    "type": "bool"
                },
                {
                    "default_value": true,
                    "description": "Strip escape characters from database names",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "strip_db_esc",
                    "type": "bool"
                },
                {
                    "description": "Username used to retrieve database users",
                    "mandatory": true,
                    "modifiable": true,
                    "name": "user",
                    "type": "string"
                },
                {
                    "description": "Load additional users from a file",
                    "mandatory": false,
                    "modifiable": false,
                    "name": "user_accounts_file",
                    "type": "path"
                },
                {
                    "default_value": "add_when_load_ok",
                    "description": "When and how the user accounts file is used",
                    "enum_values": [
                        "add_when_load_ok",
                        "file_only_always"
                    ],
                    "mandatory": false,
                    "modifiable": false,
                    "name": "user_accounts_file_usage",
                    "type": "enum"
                },
                {
                    "description": "Custom version string to use",
                    "mandatory": false,
                    "modifiable": true,
                    "name": "version_string",
                    "type": "string"
                }
            ],
            "version": "V1.1.0"
        },
        "id": "readwritesplit",
        "links": {
            "self": "http://localhost:8989/v1/modules/readwritesplit/"
        },
        "type": "modules"
    },
    "links": {
        "self": "http://localhost:8989/v1/maxscale/modules/"
    }
}
```

### Get all loaded modules

```
GET /v1/maxscale/modules
```

Retrieve information about all loaded modules.

This endpoint supports the `load=all` parameter. When defined, all modules\
located in the MaxScale module directory (`libdir`) will be loaded. This allows\
one to see the parameters of a module before the object is created.

**Response**

`Status: 200 OK`

```
{
    "data": [
        {
            "attributes": {
                "commands": [],
                "description": "maxscale",
                "maturity": "GA",
                "module_type": "maxscale",
                "parameters": [
                    {
                        "default_value": true,
                        "description": "Admin interface authentication.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_auth",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Admin interface is enabled.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_enabled",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Enable admin GUI.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_gui",
                        "type": "bool"
                    },
                    {
                        "default_value": "127.0.0.1",
                        "description": "Admin interface host.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_host",
                        "type": "string"
                    },
                    {
                        "default_value": true,
                        "description": "Log admin interface authentication failures.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "admin_log_auth_failures",
                        "type": "bool"
                    },
                    {
                        "description": "PAM service for read-only users.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_pam_readonly_service",
                        "type": "string"
                    },
                    {
                        "description": "PAM service for read-write users.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_pam_readwrite_service",
                        "type": "string"
                    },
                    {
                        "default_value": 8989,
                        "description": "Admin interface port.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_port",
                        "type": "int"
                    },
                    {
                        "default_value": true,
                        "description": "Only serve GUI over HTTPS.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_secure_gui",
                        "type": "bool"
                    },
                    {
                        "description": "Admin SSL CA cert",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_ssl_ca_cert",
                        "type": "string"
                    },
                    {
                        "description": "Admin SSL cert",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_ssl_cert",
                        "type": "string"
                    },
                    {
                        "description": "Admin SSL key",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_ssl_key",
                        "type": "string"
                    },
                    {
                        "default_value": "MAX",
                        "description": "Minimum required TLS protocol version for the REST API",
                        "enum_values": [
                            "MAX",
                            "TLSv10",
                            "TLSv11",
                            "TLSv12",
                            "TLSv13"
                        ],
                        "mandatory": false,
                        "modifiable": false,
                        "name": "admin_ssl_version",
                        "type": "enum"
                    },
                    {
                        "default_value": "10000ms",
                        "description": "Connection timeout for fetching user accounts.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "auth_connect_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "10000ms",
                        "description": "Read timeout for fetching user accounts (deprecated).",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "auth_read_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "10000ms",
                        "description": "Write timeout for fetching user accounts (deprecated).",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "auth_write_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "description": "Cluster used for configuration synchronization. If left empty (i.e. value is \"\"), synchronization is not done.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "config_sync_cluster",
                        "type": "string"
                    },
                    {
                        "default_value": "mysql",
                        "description": "Database where the 'maxscale_config' table is created.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "config_sync_db",
                        "type": "string"
                    },
                    {
                        "default_value": "5000ms",
                        "description": "How often to synchronize the configuration.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "config_sync_interval",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "description": "Password for the user used for configuration synchronization.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "config_sync_password",
                        "type": "string"
                    },
                    {
                        "default_value": "10000ms",
                        "description": "Timeout for the configuration synchronization operations.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "config_sync_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "description": "User account used for configuration synchronization.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "config_sync_user",
                        "type": "string"
                    },
                    {
                        "description": "Debug options",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "debug",
                        "type": "string"
                    },
                    {
                        "default_value": "never",
                        "description": "In what circumstances should the last statements that a client sent be dumped.",
                        "enum_values": [
                            "on_close",
                            "on_error",
                            "never"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "dump_last_statements",
                        "type": "enum"
                    },
                    {
                        "default_value": true,
                        "description": "Specifies whether persisted configuration files should be loaded on startup.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "load_persisted_configs",
                        "type": "bool"
                    },
                    {
                        "description": "Local address to use when connecting.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "local_address",
                        "type": "string"
                    },
                    {
                        "default_value": false,
                        "description": "Specifies whether debug messages should be logged (meaningful only with debug builds).",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_debug",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Specifies whether info messages should be logged.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_info",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Specifies whether notice messages should be logged.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_notice",
                        "type": "bool"
                    },
                    {
                        "default_value": {
                            "count": 10,
                            "suppress": 10000,
                            "window": 1000
                        },
                        "description": "Limit the amount of identical log messages than can be logged during a certain time period.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_throttling",
                        "type": "throttling"
                    },
                    {
                        "default_value": false,
                        "description": "Log a warning when a user with super privilege logs in.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "log_warn_super_user",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Specifies whether warning messages should be logged.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_warning",
                        "type": "bool"
                    },
                    {
                        "default_value": 10,
                        "description": "The maximum number of authentication failures that are tolerated before a host is temporarily blocked.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_auth_errors_until_block",
                        "type": "int"
                    },
                    {
                        "default_value": true,
                        "description": "Log to MaxScale's own log.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "maxlog",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Enable or disable high precision timestamps.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ms_timestamp",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "True if MaxScale is in passive mode.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "passive",
                        "type": "bool"
                    },
                    {
                        "default_value": "qc_sqlite",
                        "description": "The name of the query classifier to load.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "query_classifier",
                        "type": "string"
                    },
                    {
                        "description": "Arguments for the query classifier.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "query_classifier_args",
                        "type": "string"
                    },
                    {
                        "default_value": 5001955123,
                        "description": "Maximum amount of memory used by query classifier cache.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "query_classifier_cache_size",
                        "type": "size"
                    },
                    {
                        "default_value": 1,
                        "description": "Number of times an interrupted query is retried.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "query_retries",
                        "type": "int"
                    },
                    {
                        "default_value": "5000ms",
                        "description": "The total timeout in seconds for any retried queries.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "query_retry_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "0ms",
                        "description": "How often should the load of the worker threads be checked and rebalancing be made.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "rebalance_period",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": 20,
                        "description": "If the difference in load between the thread with the maximum load and the thread with the minimum load is larger than the value of this parameter, then work will be moved from the former to the latter.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "rebalance_threshold",
                        "type": "int"
                    },
                    {
                        "default_value": 10,
                        "description": "The load of how many seconds should be taken into account when rebalancing.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "rebalance_window",
                        "type": "count"
                    },
                    {
                        "default_value": 0,
                        "description": "How many statements should be retained for each session for debugging purposes.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "retain_last_statements",
                        "type": "count"
                    },
                    {
                        "default_value": 0,
                        "description": "How many log entries are stored in the session specific trace log.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "session_trace",
                        "type": "count"
                    },
                    {
                        "default_value": false,
                        "description": "Do not resolve client IP addresses to hostnames during authentication",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "skip_name_resolve",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Skip service and monitor permission checks.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "skip_permission_checks",
                        "type": "bool"
                    },
                    {
                        "default_value": "default",
                        "description": "The query classifier sql mode.",
                        "enum_values": [
                            "default",
                            "oracle"
                        ],
                        "mandatory": false,
                        "modifiable": false,
                        "name": "sql_mode",
                        "type": "enum"
                    },
                    {
                        "default_value": true,
                        "description": "Log to syslog.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "syslog",
                        "type": "bool"
                    },
                    {
                        "default_value": 8,
                        "description": "This parameter specifies how many threads will be used for handling the routing.",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "threads",
                        "type": "count"
                    },
                    {
                        "default_value": "0ms",
                        "description": "How often the users will be refreshed.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "users_refresh_interval",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "30000ms",
                        "description": "How often the users can be refreshed.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "users_refresh_time",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": 16777216,
                        "description": "High water mark of dcb write queue.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "writeq_high_water",
                        "type": "size"
                    },
                    {
                        "default_value": 8192,
                        "description": "Low water mark of dcb write queue.",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "writeq_low_water",
                        "type": "size"
                    }
                ],
                "version": "6.4.7"
            },
            "id": "maxscale",
            "links": {
                "self": "http://localhost:8989/v1/modules/maxscale/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "commands": [],
                "description": "servers",
                "maturity": "GA",
                "module_type": "servers",
                "parameters": [
                    {
                        "description": "Server address",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "address",
                        "type": "string"
                    },
                    {
                        "description": "Server authenticator (deprecated)",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "authenticator",
                        "type": "string"
                    },
                    {
                        "description": "Server disk space threshold",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "disk_space_threshold",
                        "type": "disk_space_limits"
                    },
                    {
                        "default_value": 0,
                        "description": "Server extra port",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "extra_port",
                        "type": "count"
                    },
                    {
                        "default_value": 0,
                        "description": "Maximum routing connections",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_routing_connections",
                        "type": "count"
                    },
                    {
                        "description": "Monitor password",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "monitorpw",
                        "type": "password"
                    },
                    {
                        "description": "Monitor user",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "monitoruser",
                        "type": "string"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Maximum time that a connection can be in the pool",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "persistmaxtime",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": 0,
                        "description": "Maximum size of the persistent connection pool",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "persistpoolmax",
                        "type": "count"
                    },
                    {
                        "default_value": 3306,
                        "description": "Server port",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "port",
                        "type": "count"
                    },
                    {
                        "default_value": 0,
                        "description": "Server priority",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "priority",
                        "type": "int"
                    },
                    {
                        "description": "Server protocol (deprecated)",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "protocol",
                        "type": "string"
                    },
                    {
                        "default_value": false,
                        "description": "Enable proxy protocol",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "proxy_protocol",
                        "type": "bool"
                    },
                    {
                        "default_value": "primary",
                        "description": "Server rank",
                        "enum_values": [
                            "primary",
                            "secondary"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "rank",
                        "type": "enum"
                    },
                    {
                        "description": "Server UNIX socket",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "socket",
                        "type": "string"
                    },
                    {
                        "default_value": false,
                        "description": "Enable TLS for server",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl",
                        "type": "bool"
                    },
                    {
                        "description": "TLS certificate authority",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_ca_cert",
                        "type": "path"
                    },
                    {
                        "description": "TLS public certificate",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_cert",
                        "type": "path"
                    },
                    {
                        "default_value": 9,
                        "description": "TLS certificate verification depth",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_cert_verify_depth",
                        "type": "count"
                    },
                    {
                        "description": "TLS cipher list",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_cipher",
                        "type": "string"
                    },
                    {
                        "description": "TLS private key",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_key",
                        "type": "path"
                    },
                    {
                        "default_value": false,
                        "description": "Verify TLS peer certificate",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_verify_peer_certificate",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Verify TLS peer host",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_verify_peer_host",
                        "type": "bool"
                    },
                    {
                        "default_value": "MAX",
                        "description": "Minimum TLS protocol version",
                        "enum_values": [
                            "MAX",
                            "TLSv10",
                            "TLSv11",
                            "TLSv12",
                            "TLSv13"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_version",
                        "type": "enum"
                    },
                    {
                        "default_value": "server",
                        "description": "Object type",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "type",
                        "type": "string"
                    }
                ],
                "version": "6.4.7"
            },
            "id": "servers",
            "links": {
                "self": "http://localhost:8989/v1/modules/servers/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "filter",
                "commands": [],
                "description": "A hint parsing filter",
                "maturity": "Alpha",
                "module_type": "Filter",
                "parameters": [],
                "version": "V1.0.0"
            },
            "id": "hintfilter",
            "links": {
                "self": "http://localhost:8989/v1/modules/hintfilter/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "authenticator",
                "commands": [],
                "description": "Standard MySQL/MariaDB authentication (mysql_native_password)",
                "maturity": "GA",
                "module_type": "Authenticator",
                "parameters": [],
                "version": "V2.1.0"
            },
            "id": "MariaDBAuth",
            "links": {
                "self": "http://localhost:8989/v1/modules/MariaDBAuth/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "monitor",
                "commands": [
                    {
                        "attributes": {
                            "arg_max": 1,
                            "arg_min": 1,
                            "description": "Fetch result of the last scheduled command.",
                            "method": "GET",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                }
                            ]
                        },
                        "id": "fetch-cmd-result",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/fetch-cmd-result/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 1,
                            "arg_min": 1,
                            "description": "Fetch result of the last scheduled command.",
                            "method": "GET",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                }
                            ]
                        },
                        "id": "fetch-cmd-results",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/fetch-cmd-results/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 1,
                            "arg_min": 1,
                            "description": "Release any held server locks for 1 minute. Does not wait for completion.",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                }
                            ]
                        },
                        "id": "async-release-locks",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/async-release-locks/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 1,
                            "arg_min": 1,
                            "description": "Release any held server locks for 1 minute.",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                }
                            ]
                        },
                        "id": "release-locks",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/release-locks/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 2,
                            "arg_min": 1,
                            "description": "Delete slave connections, delete binary logs and set up replication (dangerous). Does not wait for completion.",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                },
                                {
                                    "description": "Master server (optional)",
                                    "required": false,
                                    "type": "[SERVER]"
                                }
                            ]
                        },
                        "id": "async-reset-replication",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/async-reset-replication/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 2,
                            "arg_min": 1,
                            "description": "Delete slave connections, delete binary logs and set up replication (dangerous)",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                },
                                {
                                    "description": "Master server (optional)",
                                    "required": false,
                                    "type": "[SERVER]"
                                }
                            ]
                        },
                        "id": "reset-replication",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/reset-replication/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 2,
                            "arg_min": 2,
                            "description": "Rejoin server to a cluster. Does not wait for completion.",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                },
                                {
                                    "description": "Joining server",
                                    "required": true,
                                    "type": "SERVER"
                                }
                            ]
                        },
                        "id": "async-rejoin",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/async-rejoin/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 2,
                            "arg_min": 2,
                            "description": "Rejoin server to a cluster",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                },
                                {
                                    "description": "Joining server",
                                    "required": true,
                                    "type": "SERVER"
                                }
                            ]
                        },
                        "id": "rejoin",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/rejoin/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 1,
                            "arg_min": 1,
                            "description": "Schedule master failover. Does not wait for completion.",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                }
                            ]
                        },
                        "id": "async-failover",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/async-failover/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 1,
                            "arg_min": 1,
                            "description": "Perform master failover",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                }
                            ]
                        },
                        "id": "failover",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/failover/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 3,
                            "arg_min": 1,
                            "description": "Schedule master switchover. Does not wait for completion",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                },
                                {
                                    "description": "New master (optional)",
                                    "required": false,
                                    "type": "[SERVER]"
                                },
                                {
                                    "description": "Current master (optional)",
                                    "required": false,
                                    "type": "[SERVER]"
                                }
                            ]
                        },
                        "id": "async-switchover",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/async-switchover/"
                        },
                        "type": "module_command"
                    },
                    {
                        "attributes": {
                            "arg_max": 3,
                            "arg_min": 1,
                            "description": "Perform master switchover",
                            "method": "POST",
                            "parameters": [
                                {
                                    "description": "Monitor name",
                                    "required": true,
                                    "type": "MONITOR"
                                },
                                {
                                    "description": "New master (optional)",
                                    "required": false,
                                    "type": "[SERVER]"
                                },
                                {
                                    "description": "Current master (optional)",
                                    "required": false,
                                    "type": "[SERVER]"
                                }
                            ]
                        },
                        "id": "switchover",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/mariadbmon/switchover/"
                        },
                        "type": "module_command"
                    }
                ],
                "description": "A MariaDB Master/Slave replication monitor",
                "maturity": "GA",
                "module_type": "Monitor",
                "parameters": [
                    {
                        "mandatory": false,
                        "name": "detect_stale_master",
                        "type": "bool"
                    },
                    {
                        "mandatory": false,
                        "name": "detect_stale_slave",
                        "type": "bool"
                    },
                    {
                        "mandatory": false,
                        "name": "detect_standalone_master",
                        "type": "bool"
                    },
                    {
                        "default_value": 5,
                        "mandatory": false,
                        "name": "failcount",
                        "type": "count"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "ignore_external_masters",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "auto_failover",
                        "type": "bool"
                    },
                    {
                        "default_value": "90s",
                        "mandatory": false,
                        "name": "failover_timeout",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "default_value": "90s",
                        "mandatory": false,
                        "name": "switchover_timeout",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "mandatory": false,
                        "name": "replication_user",
                        "type": "string"
                    },
                    {
                        "mandatory": false,
                        "name": "replication_password",
                        "type": "password string"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "replication_master_ssl",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "mandatory": false,
                        "name": "verify_master_failure",
                        "type": "bool"
                    },
                    {
                        "default_value": "10s",
                        "mandatory": false,
                        "name": "master_failure_timeout",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "auto_rejoin",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "enforce_read_only_slaves",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "enforce_writable_master",
                        "type": "bool"
                    },
                    {
                        "mandatory": false,
                        "name": "servers_no_promotion",
                        "type": "serverlist"
                    },
                    {
                        "mandatory": false,
                        "name": "promotion_sql_file",
                        "type": "path"
                    },
                    {
                        "mandatory": false,
                        "name": "demotion_sql_file",
                        "type": "path"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "switchover_on_low_disk_space",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "mandatory": false,
                        "name": "maintenance_on_low_disk_space",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "mandatory": false,
                        "name": "handle_events",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "mandatory": false,
                        "name": "assume_unique_hostnames",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "mandatory": false,
                        "name": "enforce_simple_topology",
                        "type": "bool"
                    },
                    {
                        "default_value": "none",
                        "enum_values": [
                            "none",
                            "majority_of_running",
                            "majority_of_all"
                        ],
                        "mandatory": false,
                        "name": "cooperative_monitoring_locks",
                        "type": "enum"
                    },
                    {
                        "default_value": "primary_monitor_master",
                        "enum_values": [
                            "none",
                            "connecting_slave",
                            "connected_slave",
                            "running_slave",
                            "primary_monitor_master"
                        ],
                        "mandatory": false,
                        "name": "master_conditions",
                        "type": "enum_mask"
                    },
                    {
                        "default_value": "none",
                        "enum_values": [
                            "linked_master",
                            "running_master",
                            "writable_master",
                            "primary_monitor_master",
                            "none"
                        ],
                        "mandatory": false,
                        "name": "slave_conditions",
                        "type": "enum_mask"
                    },
                    {
                        "default_value": -1,
                        "mandatory": false,
                        "name": "script_max_replication_lag",
                        "type": "int"
                    },
                    {
                        "mandatory": true,
                        "name": "user",
                        "type": "string"
                    },
                    {
                        "mandatory": true,
                        "name": "password",
                        "type": "password string"
                    },
                    {
                        "default_value": "2000ms",
                        "mandatory": false,
                        "name": "monitor_interval",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "3s",
                        "mandatory": false,
                        "name": "backend_connect_timeout",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "default_value": "3s",
                        "mandatory": false,
                        "name": "backend_read_timeout",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "default_value": "3s",
                        "mandatory": false,
                        "name": "backend_write_timeout",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "default_value": 1,
                        "mandatory": false,
                        "name": "backend_connect_attempts",
                        "type": "count"
                    },
                    {
                        "default_value": "28800s",
                        "mandatory": false,
                        "name": "journal_max_age",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "mandatory": false,
                        "name": "disk_space_threshold",
                        "type": "string"
                    },
                    {
                        "default_value": "0ms",
                        "mandatory": false,
                        "name": "disk_space_check_interval",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "mandatory": false,
                        "name": "script",
                        "type": "string"
                    },
                    {
                        "default_value": "90s",
                        "mandatory": false,
                        "name": "script_timeout",
                        "type": "duration",
                        "unit": "s"
                    },
                    {
                        "default_value": "all",
                        "enum_values": [
                            "all",
                            "master_down",
                            "master_up",
                            "slave_down",
                            "slave_up",
                            "server_down",
                            "server_up",
                            "synced_down",
                            "synced_up",
                            "donor_down",
                            "donor_up",
                            "lost_master",
                            "lost_slave",
                            "lost_synced",
                            "lost_donor",
                            "new_master",
                            "new_slave",
                            "new_synced",
                            "new_donor",
                            "relay_up",
                            "relay_down",
                            "lost_relay",
                            "new_relay",
                            "blr_up",
                            "blr_down",
                            "lost_blr",
                            "new_blr"
                        ],
                        "mandatory": false,
                        "name": "events",
                        "type": "enum_mask"
                    }
                ],
                "version": "V1.5.0"
            },
            "id": "mariadbmon",
            "links": {
                "self": "http://localhost:8989/v1/modules/mariadbmon/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "protocol",
                "commands": [],
                "description": "The client to MaxScale MySQL protocol implementation",
                "maturity": "GA",
                "module_type": "Protocol",
                "parameters": [
                    {
                        "default_value": "::",
                        "description": "Listener address",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "address",
                        "type": "string"
                    },
                    {
                        "description": "Listener authenticator",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "authenticator",
                        "type": "string"
                    },
                    {
                        "description": "Authenticator options",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "authenticator_options",
                        "type": "string"
                    },
                    {
                        "description": "Path to connection initialization SQL",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "connection_init_sql_file",
                        "type": "path"
                    },
                    {
                        "default_value": 0,
                        "description": "Listener port",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "port",
                        "type": "count"
                    },
                    {
                        "default_value": "MariaDBProtocol",
                        "description": "Listener protocol to use",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "protocol",
                        "type": "module"
                    },
                    {
                        "description": "Service to which the listener connects to",
                        "mandatory": true,
                        "modifiable": false,
                        "name": "service",
                        "type": "service"
                    },
                    {
                        "description": "Listener UNIX socket",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "socket",
                        "type": "string"
                    },
                    {
                        "default_value": "default",
                        "description": "SQL parsing mode",
                        "enum_values": [
                            "default",
                            "oracle"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "sql_mode",
                        "type": "enum"
                    },
                    {
                        "default_value": false,
                        "description": "Enable TLS for server",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl",
                        "type": "bool"
                    },
                    {
                        "description": "TLS certificate authority",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_ca_cert",
                        "type": "path"
                    },
                    {
                        "description": "TLS public certificate",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_cert",
                        "type": "path"
                    },
                    {
                        "default_value": 9,
                        "description": "TLS certificate verification depth",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_cert_verify_depth",
                        "type": "count"
                    },
                    {
                        "description": "TLS cipher list",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_cipher",
                        "type": "string"
                    },
                    {
                        "description": "TLS certificate revocation list",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_crl",
                        "type": "string"
                    },
                    {
                        "description": "TLS private key",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_key",
                        "type": "path"
                    },
                    {
                        "default_value": false,
                        "description": "Verify TLS peer certificate",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_verify_peer_certificate",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Verify TLS peer host",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_verify_peer_host",
                        "type": "bool"
                    },
                    {
                        "default_value": "MAX",
                        "description": "Minimum TLS protocol version",
                        "enum_values": [
                            "MAX",
                            "TLSv10",
                            "TLSv11",
                            "TLSv12",
                            "TLSv13"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "ssl_version",
                        "type": "enum"
                    },
                    {
                        "description": "Path to user and group mapping file",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "user_mapping_file",
                        "type": "path"
                    }
                ],
                "version": "V1.1.0"
            },
            "id": "MariaDBProtocol",
            "links": {
                "self": "http://localhost:8989/v1/modules/MariaDBProtocol/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "query_classifier",
                "commands": [],
                "description": "Query classifier using sqlite.",
                "maturity": "GA",
                "module_type": "QueryClassifier",
                "parameters": [],
                "version": "V1.0.0"
            },
            "id": "qc_sqlite",
            "links": {
                "self": "http://localhost:8989/v1/modules/qc_sqlite/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "filter",
                "commands": [
                    {
                        "attributes": {
                            "arg_max": 3,
                            "arg_min": 1,
                            "description": "Show unified log file as a JSON array",
                            "method": "GET",
                            "parameters": [
                                {
                                    "description": "Filter to read logs from",
                                    "required": true,
                                    "type": "FILTER"
                                },
                                {
                                    "description": "Start reading from this line",
                                    "required": false,
                                    "type": "[STRING]"
                                },
                                {
                                    "description": "Stop reading at this line (exclusive)",
                                    "required": false,
                                    "type": "[STRING]"
                                }
                            ]
                        },
                        "id": "log",
                        "links": {
                            "self": "http://localhost:8989/v1/modules/qlafilter/log/"
                        },
                        "type": "module_command"
                    }
                ],
                "description": "A simple query logging filter",
                "maturity": "GA",
                "module_type": "Filter",
                "parameters": [
                    {
                        "default_value": true,
                        "description": "Append new entries to log files instead of overwriting them",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "append",
                        "type": "bool"
                    },
                    {
                        "default_value": "ms",
                        "description": "Duration in milliseconds (ms) or microseconds (us)",
                        "enum_values": [
                            "ms",
                            "milliseconds",
                            "us",
                            "microseconds"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "duration_unit",
                        "type": "enum"
                    },
                    {
                        "description": "Exclude queries matching this pattern from the log",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "exclude",
                        "type": "regex"
                    },
                    {
                        "description": "The basename of the output file",
                        "mandatory": true,
                        "modifiable": true,
                        "name": "filebase",
                        "type": "string"
                    },
                    {
                        "default_value": false,
                        "description": "Flush log files after every write",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "flush",
                        "type": "bool"
                    },
                    {
                        "default_value": "date,user,query",
                        "description": "Type of data to log in the log files",
                        "enum_values": [
                            "service",
                            "session",
                            "date",
                            "user",
                            "query",
                            "reply_time",
                            "total_reply_time",
                            "default_db",
                            "num_rows",
                            "reply_size",
                            "transaction",
                            "transaction_time",
                            "num_warnings",
                            "error_msg"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_data",
                        "type": "enum_mask"
                    },
                    {
                        "default_value": "session",
                        "description": "The type of log file to use",
                        "enum_values": [
                            "session",
                            "unified",
                            "stdout"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_type",
                        "type": "enum_mask"
                    },
                    {
                        "description": "Only log queries matching this pattern",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "match",
                        "type": "regex"
                    },
                    {
                        "default_value": " ",
                        "description": "Value used to replace newlines",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "newline_replacement",
                        "type": "string"
                    },
                    {
                        "default_value": "",
                        "description": "Regular expression options",
                        "enum_values": [
                            "case",
                            "ignorecase",
                            "extended"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "options",
                        "type": "enum_mask"
                    },
                    {
                        "default_value": ",",
                        "description": "Defines the separator between elements of a log entry",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "separator",
                        "type": "string"
                    },
                    {
                        "description": "Log queries only from this network address",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "source",
                        "type": "string"
                    },
                    {
                        "default_value": false,
                        "description": "Write queries in canonical form",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "use_canonical_form",
                        "type": "bool"
                    },
                    {
                        "description": "Log queries only from this user",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "user",
                        "type": "string"
                    }
                ],
                "version": "V1.1.1"
            },
            "id": "qlafilter",
            "links": {
                "self": "http://localhost:8989/v1/modules/qlafilter/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "router",
                "commands": [],
                "description": "A connection based router to load balance based on connections",
                "maturity": "GA",
                "module_type": "Router",
                "parameters": [
                    {
                        "default_value": true,
                        "description": "Use master for reads",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "master_accept_reads",
                        "type": "bool"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Maximum acceptable replication lag",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_replication_lag",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "running",
                        "description": "A comma separated list of server roles",
                        "enum_values": [
                            "master",
                            "slave",
                            "running",
                            "synced"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "router_options",
                        "type": "enum_mask"
                    },
                    {
                        "default_value": false,
                        "description": "Retrieve users from all backend servers instead of only one",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "auth_all_servers",
                        "type": "bool"
                    },
                    {
                        "default_value": "300000ms",
                        "description": "How ofted idle connections are pinged",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "connection_keepalive",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Connection idle timeout",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "connection_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": false,
                        "description": "Disable session command history",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "disable_sescmd_history",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Allow the root user to connect to this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "enable_root_user",
                        "type": "bool"
                    },
                    {
                        "default_value": "-1ms",
                        "description": "Put connections into pool after session has been idle for this long",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "idle_session_pool_time",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": true,
                        "description": "Match localhost to wildcard host",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "localhost_match_wildcard_host",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Log a warning when client authentication fails",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_auth_warnings",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log debug messages for this service (debug builds only)",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_debug",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log info messages for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_info",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log notice messages for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_notice",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log warning messages for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_warning",
                        "type": "bool"
                    },
                    {
                        "default_value": 0,
                        "description": "Maximum number of connections",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_connections",
                        "type": "count"
                    },
                    {
                        "default_value": 50,
                        "description": "Session command history size",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_sescmd_history",
                        "type": "count"
                    },
                    {
                        "default_value": "60000ms",
                        "description": "How long a session can wait for a connection to become available",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "multiplex_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Network write timeout",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "net_write_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "description": "Password for the user used to retrieve database users",
                        "mandatory": true,
                        "modifiable": true,
                        "name": "password",
                        "type": "string"
                    },
                    {
                        "default_value": true,
                        "description": "Prune old session command history if the limit is exceeded",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "prune_sescmd_history",
                        "type": "bool"
                    },
                    {
                        "default_value": "primary",
                        "description": "Service rank",
                        "enum_values": [
                            "primary",
                            "secondary"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "rank",
                        "type": "enum"
                    },
                    {
                        "default_value": -1,
                        "description": "Number of statements kept in memory",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "retain_last_statements",
                        "type": "int"
                    },
                    {
                        "default_value": false,
                        "description": "Enable session tracing for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "session_trace",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Track session state using server responses",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "session_track_trx_state",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Strip escape characters from database names",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "strip_db_esc",
                        "type": "bool"
                    },
                    {
                        "description": "Username used to retrieve database users",
                        "mandatory": true,
                        "modifiable": true,
                        "name": "user",
                        "type": "string"
                    },
                    {
                        "description": "Load additional users from a file",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "user_accounts_file",
                        "type": "path"
                    },
                    {
                        "default_value": "add_when_load_ok",
                        "description": "When and how the user accounts file is used",
                        "enum_values": [
                            "add_when_load_ok",
                            "file_only_always"
                        ],
                        "mandatory": false,
                        "modifiable": false,
                        "name": "user_accounts_file_usage",
                        "type": "enum"
                    },
                    {
                        "description": "Custom version string to use",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "version_string",
                        "type": "string"
                    }
                ],
                "version": "V2.0.0"
            },
            "id": "readconnroute",
            "links": {
                "self": "http://localhost:8989/v1/modules/readconnroute/"
            },
            "type": "modules"
        },
        {
            "attributes": {
                "api": "router",
                "commands": [],
                "description": "A Read/Write splitting router for enhancement read scalability",
                "maturity": "GA",
                "module_type": "Router",
                "parameters": [
                    {
                        "default_value": "false",
                        "description": "Causal reads mode",
                        "enum_values": [
                            "false",
                            "off",
                            "0",
                            "true",
                            "on",
                            "1",
                            "none",
                            "local",
                            "global",
                            "fast"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "causal_reads",
                        "type": "enum"
                    },
                    {
                        "default_value": "10000ms",
                        "description": "Timeout for the slave synchronization",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "causal_reads_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": false,
                        "description": "Retry failed writes outside of transactions",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "delayed_retry",
                        "type": "bool"
                    },
                    {
                        "default_value": "10000ms",
                        "description": "Timeout for delayed_retry",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "delayed_retry_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": false,
                        "description": "Create connections only when needed",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "lazy_connect",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Use master for reads",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "master_accept_reads",
                        "type": "bool"
                    },
                    {
                        "default_value": "fail_instantly",
                        "description": "Master failure mode behavior",
                        "enum_values": [
                            "fail_instantly",
                            "fail_on_write",
                            "error_on_write"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "master_failure_mode",
                        "type": "enum"
                    },
                    {
                        "default_value": false,
                        "description": "Reconnect to master",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "master_reconnection",
                        "type": "bool"
                    },
                    {
                        "default_value": 255,
                        "description": "Maximum number of slave connections",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_slave_connections",
                        "type": "count"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Maximum allowed slave replication lag",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_slave_replication_lag",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": false,
                        "description": "Optimistically offload transactions to slaves",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "optimistic_trx",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Automatically retry failed reads outside of transactions",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "retry_failed_reads",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Reuse identical prepared statements inside the same connection",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "reuse_prepared_statements",
                        "type": "bool"
                    },
                    {
                        "default_value": 255,
                        "description": "Starting number of slave connections",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "slave_connections",
                        "type": "count"
                    },
                    {
                        "default_value": "LEAST_CURRENT_OPERATIONS",
                        "description": "Slave selection criteria",
                        "enum_values": [
                            "LEAST_GLOBAL_CONNECTIONS",
                            "LEAST_ROUTER_CONNECTIONS",
                            "LEAST_BEHIND_MASTER",
                            "LEAST_CURRENT_OPERATIONS",
                            "ADAPTIVE_ROUTING"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "slave_selection_criteria",
                        "type": "enum"
                    },
                    {
                        "default_value": false,
                        "description": "Lock connection to master after multi-statement query",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "strict_multi_stmt",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Lock connection to master after a stored procedure is executed",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "strict_sp_calls",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Retry failed transactions",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "transaction_replay",
                        "type": "bool"
                    },
                    {
                        "default_value": 5,
                        "description": "Maximum number of times to retry a transaction",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "transaction_replay_attempts",
                        "type": "count"
                    },
                    {
                        "default_value": "full",
                        "description": "Type of checksum to calculate for results",
                        "enum_values": [
                            "full",
                            "result_only",
                            "no_insert_id"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "transaction_replay_checksum",
                        "type": "enum"
                    },
                    {
                        "default_value": 1048576,
                        "description": "Maximum size of transaction to retry",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "transaction_replay_max_size",
                        "type": "size"
                    },
                    {
                        "default_value": false,
                        "description": "Retry transaction on deadlock",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "transaction_replay_retry_on_deadlock",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Retry transaction on checksum mismatch",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "transaction_replay_retry_on_mismatch",
                        "type": "bool"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Timeout for transaction replay",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "transaction_replay_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "all",
                        "description": "Whether to route SQL variable modifications to all servers or only to the master",
                        "enum_values": [
                            "all",
                            "master"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "use_sql_variables_in",
                        "type": "enum"
                    },
                    {
                        "default_value": false,
                        "description": "Retrieve users from all backend servers instead of only one",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "auth_all_servers",
                        "type": "bool"
                    },
                    {
                        "default_value": "300000ms",
                        "description": "How ofted idle connections are pinged",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "connection_keepalive",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Connection idle timeout",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "connection_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": false,
                        "description": "Disable session command history",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "disable_sescmd_history",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Allow the root user to connect to this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "enable_root_user",
                        "type": "bool"
                    },
                    {
                        "default_value": "-1ms",
                        "description": "Put connections into pool after session has been idle for this long",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "idle_session_pool_time",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": true,
                        "description": "Match localhost to wildcard host",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "localhost_match_wildcard_host",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Log a warning when client authentication fails",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_auth_warnings",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log debug messages for this service (debug builds only)",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_debug",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log info messages for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_info",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log notice messages for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_notice",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Log warning messages for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "log_warning",
                        "type": "bool"
                    },
                    {
                        "default_value": 0,
                        "description": "Maximum number of connections",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_connections",
                        "type": "count"
                    },
                    {
                        "default_value": 50,
                        "description": "Session command history size",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "max_sescmd_history",
                        "type": "count"
                    },
                    {
                        "default_value": "60000ms",
                        "description": "How long a session can wait for a connection to become available",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "multiplex_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "default_value": "0ms",
                        "description": "Network write timeout",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "net_write_timeout",
                        "type": "duration",
                        "unit": "ms"
                    },
                    {
                        "description": "Password for the user used to retrieve database users",
                        "mandatory": true,
                        "modifiable": true,
                        "name": "password",
                        "type": "string"
                    },
                    {
                        "default_value": true,
                        "description": "Prune old session command history if the limit is exceeded",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "prune_sescmd_history",
                        "type": "bool"
                    },
                    {
                        "default_value": "primary",
                        "description": "Service rank",
                        "enum_values": [
                            "primary",
                            "secondary"
                        ],
                        "mandatory": false,
                        "modifiable": true,
                        "name": "rank",
                        "type": "enum"
                    },
                    {
                        "default_value": -1,
                        "description": "Number of statements kept in memory",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "retain_last_statements",
                        "type": "int"
                    },
                    {
                        "default_value": false,
                        "description": "Enable session tracing for this service",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "session_trace",
                        "type": "bool"
                    },
                    {
                        "default_value": false,
                        "description": "Track session state using server responses",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "session_track_trx_state",
                        "type": "bool"
                    },
                    {
                        "default_value": true,
                        "description": "Strip escape characters from database names",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "strip_db_esc",
                        "type": "bool"
                    },
                    {
                        "description": "Username used to retrieve database users",
                        "mandatory": true,
                        "modifiable": true,
                        "name": "user",
                        "type": "string"
                    },
                    {
                        "description": "Load additional users from a file",
                        "mandatory": false,
                        "modifiable": false,
                        "name": "user_accounts_file",
                        "type": "path"
                    },
                    {
                        "default_value": "add_when_load_ok",
                        "description": "When and how the user accounts file is used",
                        "enum_values": [
                            "add_when_load_ok",
                            "file_only_always"
                        ],
                        "mandatory": false,
                        "modifiable": false,
                        "name": "user_accounts_file_usage",
                        "type": "enum"
                    },
                    {
                        "description": "Custom version string to use",
                        "mandatory": false,
                        "modifiable": true,
                        "name": "version_string",
                        "type": "string"
                    }
                ],
                "version": "V1.1.0"
            },
            "id": "readwritesplit",
            "links": {
                "self": "http://localhost:8989/v1/modules/readwritesplit/"
            },
            "type": "modules"
        }
    ],
    "links": {
        "self": "http://localhost:8989/v1/maxscale/modules/"
    }
}
```

### Call a module command

For read-only commands:

```
GET /v1/maxscale/modules/:module/:command
```

For commands that can modify data:

```
POST /v1/maxscale/modules/:module/:command
```

Modules can expose commands that can be called via the REST API. The module\
resource lists all commands in the `data.attributes.commands` list. Each value\
is a command sub-resource identified by its `id` field and the HTTP method the\
command uses is defined by the `attributes.method` field.

The _:module_ in the URI must be a valid name of a loaded module and _:command_\
must be a valid command identifier that is exposed by that module. All\
parameters to the module commands are passed as HTTP request parameters.

Here is an example POST requests to the dbfwfilter module command _reload_ with\
two parameters, the name of the filter instance and the path to a file:

```
POST /v1/maxscale/modules/dbfwfilter/reload?my-dbfwfilter-instance&/path/to/file.txt
```

**Response**

Command with output:

`Status: 200 OK`

```
{
    "links": {
        "self": "http://localhost:8989/v1/maxscale/modules/dbfwfilter/rules/json"
    },
    "meta": [ // Output of module command (module dependent)
        {
            "name": "test3",
            "type": "COLUMN",
            "times_matched": 0
        }
    ]
}
```

The contents of the `meta` field will contain the output of the module\
command. This output depends on the command that is being executed. It can\
contain any valid JSON value.

Command with no output:

`Status: 204 No Content`

### Classify a statement

```
GET /v1/maxscale/query_classifier/classify?sql=<statement>
```

Classify provided statement and return the result.

**Response**

`Status: 200 OK`

```
GET /v1/maxscale/query_classifier/classify?sql=SELECT+1
```

```
{
    "data": {
        "attributes": {
            "canonical": "SELECT ?",
            "fields": [],
            "functions": [],
            "has_where_clause": false,
            "operation": "QUERY_OP_SELECT",
            "parse_result": "QC_QUERY_PARSED",
            "type_mask": "QUERY_TYPE_READ"
        },
        "id": "classify",
        "type": "classify"
    },
    "links": {
        "self": "http://localhost:8989/v1/maxscale/query_classifier/classify/"
    }
}
```

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
