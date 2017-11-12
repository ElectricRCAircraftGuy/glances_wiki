**Only for Glances v2.1 or higher !**

Glances HTTP API is based on **RESTFul/JSON**.

# Serveur side

    $ glances -w

    Glances Web server is running on 0.0.0.0:61208

# Client side

The RESTful API is located at:

`http://{glances server IP@}:61208/api/2`

Request example with Curl:

    $ curl http://localhost:61208/api/2/mem
    {"available": 3627708416, "used": 4244357120, "cached": 2746822656, "percent": 53.9, "free": 3627708416, "inactive": 2100039680, "active": 4159094784, "shared": 384692224, "total": 7872065536, "buffers": 395943936}

Or with Httpie:

```
$ http http://localhost:61208/api/2/mem
HTTP/1.0 200 OK
Access-Control-Allow-Headers: Origin, Accept, Content-Type, X-Requested-With, X-CSRF-Token
Access-Control-Allow-Methods: GET, POST, PUT, OPTIONS
Access-Control-Allow-Origin: *
Content-Encoding: gzip
Content-Type: application/json
Date: Sun, 12 Nov 2017 16:06:10 GMT
Server: WSGIServer/0.1 Python/2.7.12

{
    "active": 4165025792, 
    "available": 3621687296, 
    "buffers": 395997184, 
    "cached": 2747146240, 
    "free": 3621687296, 
    "inactive": 2100359168, 
    "percent": 54.0, 
    "shared": 385015808, 
    "total": 7872065536, 
    "used": 4250378240
}
```

From Glances version 3 and higher, support of Gzip encoding is provided (active by default with Httpie). For Curl, add the followings tags:

    $ curl -H "Accept-encoding: gzip" --compressed -v http://localhost:61208/api/2/all
    < Content-Encoding: gzip

***

### GET _**/api/2/pluginslist**_

Return the plugins available on the Glances server.

Request parameters: 

* None

Request response:

* 200 - application/json: list
* 404 - Returned if the property does not exist

Example: _/api/2/pluginslist_

```
["load", "core", "uptime", "fs", "memswap", "monitor", "percpu", "mem", "sensors", "system", "alert", "psutilversion", "processlist", "diskio", "hddtemp", "processcount", "batpercent", "now", "cpu", "network", "help"]
```

***

### GET _**/api/2/:plugin**_

Return the stats for the specific ``plugin``

Request parameters: 

* plugin: plugin name

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/mem_

```
{"available": 5071183872, "used": 3255848960, "cached": 1827352576, "percent": 39.1, "free": 5071183872, "inactive": 1388982272, "active": 3679604736, "total": 8327032832, "buffers": 477982720}
```

***

### GET _**/api/2/:plugin/:item**_

Return the ``item`` stat for the specific ``plugin``

Request parameters: 

* plugin: plugin name
* item: item to retrieve

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/mem/used_

Return the memory used (RAM)
```
{"used": 3255848960}
```

Example: _/api/2/processlist/pid_

Return processes' pid list
```
{"pid": [1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 72, 73, 74, 75, 76, 77, 78, 90, 92, 93, 113, 114, 165, 167, 168, 169, 170, 171, 172, 191, 192, 370, 376, 429, 430, 454, 468, 522, 562, 770, 773]}
```

Example: _/api/2/network/interface_name_

Return network interfaces name list

```
{"interface_name": ["lo", "docker0", "eth0"]}
```

***

### GET _**/api/2/:plugin/:item/:value**_

Return the ``item``==``value`` stat for the specific ``plugin``

Request parameters: 

* plugin: plugin name
* item: item to retrieve
* value: filter on item value 

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/processlist/pid/770_

Return process stats for pid 770
```
{"770": [{"username": "messagebus", "status": "S", "cpu_times": [0.17, 0.04], "name": "dbus-daemon", "memory_percent": 0.031136757261677143, "cpu_percent": 0.0, "pid": 770, "ppid": 768, "io_counters": [0, 0, 0, 0, 0], "cmdline": "dbus-daemon --system --fork", "memory_info": [2592768, 41635840], "time_since_update": 59.427401065826416, "nice": 0}]}
```

Example: _/api/2/network/interface_name/eth0_

Return eth0 network interface stats

```
{"eth0": [{"tx": 233589, "cumulative_rx": 225276411, "rx": 510828, "cumulative_cx": 251558670, "time_since_update": 287.83594512939453, "cx": 744417, "cumulative_tx": 26282259, "interface_name": "eth0"}]}
```

***

### GET _**/api/2/all**_

Return all availables stats

Request parameters: 

* None

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/all_

```
{"load": {"cpucore": 4, "min1": 0.18, "min5": 0.29, "min15": 0.36}, "core": {"phys": 1, "log": 4}, "uptime": "7:10:12", "fs": [{"mnt_point": "/", "used": 164121161728, "percent": 76.3, "device_name": "/dev/sda5", "fs_type": "ext4", "size": 215225925632}],...}
```

***

### GET _**/api/2/:plugin/history**_

Return the history stats for the specific ``plugin``

**Only available in Glances 2.7 or higher**

Request parameters: 

* plugin: plugin name

Request response:

* 200 - application/json: dict of list of tuple (timestamp, value)
* 404 - Returned if the property does not exist

Example: _/api/2/cpu/history_

```
{"user": [["2016-06-02T17:44:48.754493", 23.3], ["2016-06-02T17:45:03.046595", 2.2], ["2016-06-02T17:45:05.582539", 5.0], ["2016-06-02T17:45:23.093514", 3.2]], "system": [["2016-06-02T17:44:48.754515", 4.0], ["2016-06-02T17:45:03.046611", 0.8], ["2016-06-02T17:45:05.582556", 2.2], ["2016-06-02T17:45:23.093532", 0.7]]}
```

***

### GET _**/api/2/:plugin/history/:nb**_

Return the latest nb history stats for the specific ``plugin``

**Only available in Glances 2.7 or higher**

Request parameters: 

* plugin: plugin name
* nb: number of history value

Request response:

* 200 - application/json: dict of list of tuple (timestamp, value)
* 404 - Returned if the property does not exist

Example: _/api/2/cpu/history/2_

```
{"user": [["2016-06-02T17:45:23.093514", 3.2], ["2016-06-02T17:47:06.390767", 2.1]], "system": [["2016-06-02T17:45:23.093532", 0.7], ["2016-06-02T17:47:06.390786", 0.2]]}
```

***

### GET _**/api/2/:plugin/:item/history**_

Return the item history stats for the specific ``plugin``

**Only available in Glances 2.7 or higher**

Request parameters: 

* plugin: plugin name
* item: item to retrieve

Request response:

* 200 - application/json: dict of list of tuple (timestamp, value)
* 404 - Returned if the property does not exist

Example: _/api/2/cpu/user/history

```
{"user": [["2016-06-02T17:49:28.822984", 2.4], ["2016-06-02T17:49:45.982829", 2.4], ["2016-06-02T17:49:49.566442", 1.5]]}
```

***

### GET _**/api/2/:plugin/:item/history/:nb**_

Return the latest nb item history stats for the specific ``plugin``

**Only available in Glances 2.7 or higher**

Request parameters: 

* plugin: plugin name
* item: item to retrieve
* nb: number of history value

Request response:

* 200 - application/json: dict of list of tuple (timestamp, value)
* 404 - Returned if the property does not exist

Example: _/api/2/cpu/user/history/2

```
{"user": [["2016-06-02T17:49:49.566442", 1.5], ["2016-06-02T17:51:20.527461", 2.4]]}
```

***

### GET _**/api/2/all/limits**_

Return all limits of the server side

Request parameters: 

* None

Request response:

* 200 - application/json: dictionnary of dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/all/limits_

```
{u'load': {u'load_critical': 5.0, u'load_careful': 0.7, u'load_warning': 1.0}, u'help': {}, u'memswap': {u'memswap_careful': 50.0, u'memswap_critical': 90.0, u'memswap_warning': 70.0}, ...
```

***

### GET _**/api/2/all/views**_

Return all views information (could be usefull to display the stats)

Request parameters: 

* None

Request response:

* 200 - application/json: dictionnary of dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/all/views_

```
{u'load': {u'cpucore': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'min1': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'min5': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'min15': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}}, u'help': {}, u'memswap': {u'used': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}, u'percent': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'free': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'sout': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'total': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'sin': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'processlist': {}, u'uptime': {}, u'monitor': {}, ...
```

***

### GET _**/api/2/:plugin/limits**_

Return the limits for the specific ``plugin``

Request parameters: 

* plugin: plugin name

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/mem/limits_

```
{"mem_careful": 50.0, "mem_critical": 90.0, "mem_warning": 70.0}
```

***

### GET _**/api/2/args**_

*New in 2.6 or +*

Return all Glances command line arguments

Request parameters: 

* None

Request response:

* 200 - application/json: dictionnary
* 404 - Returned if the property does not exist

Example: _/api/2/args_

```
{"full_quicklook": false, "snmp_version": "2c", "network_cumul": false, "help_tag": false, "snmp_port": 161, "export_csv": null, "export_statsd": false, "network_sum": false, "enable_process_extended": false, "process_short_name": true, "snmp_community": "public", "disable_sensors": false
```

***

### GET _**/api/2/args/:item**_

*New in 2.6 or +*

Return Glances command line argument for the given item

Request parameters: 

* None

Request response:

* 200 - application/json: dictionnary
* 400 - Item did not exist
* 404 - Returned if the property does not exist

Example: Return the refresh time _/api/2/args/time_

```
5
```

***