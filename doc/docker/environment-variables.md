## Environment variables

### General

* `TZ`: The timezone assigned to the container (default `UTC`)
* `PUID`: LibreNMS user id (default `1000`)
* `PGID`: LibreNMS group id (default `1000`)
* `MEMORY_LIMIT`: PHP memory limit (default `256M`)
* `UPLOAD_MAX_SIZE`: Upload max size (default `16M`)
* `OPCACHE_MEM_SIZE`: PHP OpCache memory consumption (default `128`)
* `LISTEN_IPV6`: Enable IPv6 for Nginx (default `true`)
* `REAL_IP_FROM`: Trusted addresses that are known to send correct replacement addresses (default `0.0.0.0/32`)
* `REAL_IP_HEADER`: Request header field whose value will be used to replace the client address (default `X-Forwarded-For`)
* `LOG_IP_VAR`: Use another variable to retrieve the remote IP address for access [log_format](http://nginx.org/en/docs/http/ngx_http_log_module.html#log_format) on Nginx. (default `remote_addr`)

### Dispatcher service

> :warning: Only used if you enable and run a [sidecar dispatcher container](../notes/dispatcher-service.md)

* `SIDECAR_DISPATCHER`: Set to `1` to enable sidecar dispatcher mode for this container (default `0`)
* `DISPATCHER_NODE_ID`: Unique node ID for your dispatcher service
* `REDIS_HOST`: Redis host for poller synchronization
* `REDIS_PORT`: Redis port (default `6379`)
* `REDIS_PASSWORD`: Redis password
* `REDIS_DB`: Redis database (default `0`)

### Distributed Poller

* `LIBRENMS_POLLER_THREADS`: Threads that `poller-wrapper.py` runs (default `16`)
* `LIBRENMS_POLLER_INTERVAL`: Interval in minutes at which `poller-wrapper.py` runs (default `5`) [docs](https://docs.librenms.org/Support/1-Minute-Polling/)
* `LIBRENMS_DISTRIBUTED_POLLER_ENABLE`: Enable distributed poller functionality
* `LIBRENMS_DISTRIBUTED_POLLER_NAME`: Optional name of poller (default `$(hostname)`)
* `LIBRENMS_DISTRIBUTED_POLLER_GROUP`: By default, all hosts are shared and have the poller_group = 0. To pin a device to a poller, set it to a value greater than 0 and set the same value here. One can also specify a comma separated string of poller groups. The poller will then poll devices from any of the groups listed. [docs](https://docs.librenms.org/Extensions/Distributed-Poller/)
* `LIBRENMS_DISTRIBUTED_POLLER_MEMCACHED_HOST`: Memcached server for poller synchronization (default `$MEMCACHED_HOST`)
* `LIBRENMS_DISTRIBUTED_POLLER_MEMCACHED_PORT`: Port of memcached server (default `$MEMCACHED_PORT`)

### Syslog-ng

> :warning: Only used if you enable and run a [sidecar syslog-ng container](../notes/syslog-ng.md)

* `SIDECAR_SYSLOGNG`: Set to `1` to enable sidecar syslog-ng mode for this container (default `0`)

### Database

* `DB_HOST`: MySQL database hostname / IP address
* `DB_PORT`: MySQL database port (default `3306`)
* `DB_NAME`: MySQL database name (default `librenms`)
* `DB_USER`: MySQL user (default `librenms`)
* `DB_PASSWORD`: MySQL password (default `librenms`)
* `DB_TIMEOUT`: Time in seconds after which we stop trying to reach the MySQL server (useful for clusters, default `60`)

### Misc

* `LIBRENMS_SNMP_COMMUNITY`: This container's SNMP v2c community string (default `librenmsdocker`)
* `LIBRENMS_WEATHERMAP`: Enable LibreNMS [Weathermap plugin](https://docs.librenms.org/Extensions/Weathermap/) (default `false`)
* `LIBRENMS_WEATHERMAP_SCHEDULE`: CRON expression format (default `*/5 * * * *`)
* `MEMCACHED_HOST`: Hostname / IP address of a Memcached server
* `MEMCACHED_PORT`: Port of the Memcached server (default `11211`)
* `RRDCACHED_HOST`: Hostname / IP address of a RRDcached server
* `RRDCACHED_PORT`: Port of the RRDcached server (default `42217`)
