# Ping plugin

A plugin with a list of hosts to monitor. Used with the client/server mode, it could be useful to monitor non visible host (from the client point of view).

For example:
```
backendserver1   OK  10ms
backendserver2   OK  8ms
```

Resources:
* https://gist.github.com/luizfb/6958733

# Memcached

A plugin to display get hit(or set) of a memcached server.

For example:

```
       Total    Hit
Get    3200     3000
Set    49       10
```

Resources:
* Use the python-memcached lib and its get_stats method

```
>>> import memcache
>>> s = memcache.Client([localhost:11211])
>>> s.get_stats()
[('localhost:11211 (1)', {'auth_cmds': '0', 'reclaimed': '0', 'pid': '5698', 'cas_hits': '0', 'uptime': '3214011', 'delete_misses': '0', 'listen_disabled_num': '0', 'cas_misses': '0', 'decr_hits': '0', 'incr_hits': '0', 'version': '1.4.5', 'limit_maxbytes': '67108864', 'bytes_written': '0', 'incr_misses': '0', 'accepting_conns': '1', 'rusage_system': '29.357834', 'total_items': '0', 'cmd_get': '0', 'curr_connections': '5', 'threads': '4', 'total_connections': '6', 'cmd_set': '0', 'curr_items': '0', 'conn_yields': '0', 'get_misses': '0', 'bytes_read': '7', 'cas_badval': '0', 'cmd_flush': '0', 'evictions': '0', 'bytes': '0', 'connection_structures': '6', 'auth_errors': '0', 'rusage_user': '20.277267', 'time': '1427670767', 'delete_hits': '0', 'pointer_size': '64', 'decr_misses': '0', 'get_hits': '0'})]
```
