**Only for Glances v2.1 or higher !**

Glances HTTP API is based on **RESTFULL/JSON**.

Serveur side
============

    $ glances -w

    Glances Web server is running on 0.0.0.0:61208

Client side
===========

***

_**/api/2/pluginslist**_

Return the plugins available on the Glances server.

Request parameters: 

* None

Request response:

* 200 - application/json: list
* 404 - Returned if the property does not exist

Example: _/api/v2/pluginslist_

```
["load", "core", "uptime", "fs", "memswap", "monitor", "percpu", "mem", "sensors", "system", "alert", "psutilversion", "processlist", "diskio", "hddtemp", "processcount", "batpercent", "now", "cpu", "network", "help"]
```

***

_**/api/2/:plugin**_

Return the stats for the specific ``plugin``

Request parameters: 

* plugin: plugin name

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/v2/mem_

```
{"available": 5071183872, "used": 3255848960, "cached": 1827352576, "percent": 39.1, "free": 5071183872, "inactive": 1388982272, "active": 3679604736, "total": 8327032832, "buffers": 477982720}
```

***

_**/api/2/:plugin/:item**_

Return the ``item`` stat for the specific ``plugin``

Request parameters: 

* plugin: plugin name
* item: item to retreive

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/v2/mem/used_

```
{"used": 3255848960}
```

***
