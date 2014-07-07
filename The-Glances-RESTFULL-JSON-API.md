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
* item: item to retrieve

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/v2/mem/used_

Return the memory used (RAM)
```
{"used": 3255848960}
```

Example: _/api/v2/processlist/pid_

Return processes' pid list
```
{"pid": [1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 72, 73, 74, 75, 76, 77, 78, 90, 92, 93, 113, 114, 165, 167, 168, 169, 170, 171, 172, 191, 192, 370, 376, 429, 430, 454, 468, 522, 562, 770, 773]}
```

Example: _/api/v2/network/interface_name_

Return network interfaces name list

```
{"interface_name": ["lo", "docker0", "eth0"]}
```

***

_**/api/2/:plugin/:item/:value**_

Return the ``item``==``value`` stat for the specific ``plugin``

Request parameters: 

* plugin: plugin name
* item: item to retrieve
* value: filter on item value 

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/v2/processlist/pid/770_

Return process stats for pid 770
```
{"770": [{"username": "messagebus", "status": "S", "cpu_times": [0.17, 0.04], "name": "dbus-daemon", "memory_percent": 0.031136757261677143, "cpu_percent": 0.0, "pid": 770, "io_counters": [0, 0, 0, 0, 0], "cmdline": "dbus-daemon --system --fork", "memory_info": [2592768, 41635840], "time_since_update": 59.427401065826416, "nice": 0}]}
```

Example: _/api/v2/network/interface_name/eth0_

Return eth0 network interface stats

```
{"eth0": [{"tx": 233589, "cumulative_rx": 225276411, "rx": 510828, "cumulative_cx": 251558670, "time_since_update": 287.83594512939453, "cx": 744417, "cumulative_tx": 26282259, "interface_name": "eth0"}]}
```

***

_**/api/2/all**_

Return all availables stats

Request parameters: 

* None

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/v2/all_

```
{"load": {"cpucore": 4, "min1": 0.18, "min5": 0.29, "min15": 0.36}, "core": {"phys": 1, "log": 4}, "uptime": "7:10:12", "fs": [{"mnt_point": "/", "used": 164121161728, "percent": 76.3, "device_name": "/dev/sda5", "fs_type": "ext4", "size": 215225925632}],...}
```

***