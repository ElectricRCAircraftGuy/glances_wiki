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

None

Request response:

* 200 - application/json: list
* 404 - Returned if the property does not exist

Example:

```
["load", "core", "uptime", "fs", "memswap", "monitor", "percpu", "mem", "sensors", "system", "alert", "psutilversion", "processlist", "diskio", "hddtemp", "processcount", "batpercent", "now", "cpu", "network", "help"]
```




