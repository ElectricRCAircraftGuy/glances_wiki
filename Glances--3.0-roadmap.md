**THIS DOCUMENT IS UNDER CONSTRUCTION**

**API COULD AND WILL CHANGE**


A deep re-factor of the Glances software architecture will be made in the version 3.0. The goal of this wiki page is to summarize the concepts and provide an overview of the software for the current and future contributors.

# Glances challenges

Glances is a cross-platform system monitoring software, its main purpose is to present a maximum of information in a minimum of space. By "minimum of space", we means only one screen (no menu, no tabs). It can adapt dynamically the displayed information depending on the user interface size. 

# Modes

3 modes are available:
- Glances standalone/client (Curse and Web based UI are provided)
- Glances server (passive mode, waiting for incoming requests from clients)
- Glances export (active mode, push stats to various endpoints)

It should be possible to start all the following modes individually or in parallel, limited to the following combinations:

- client + server
- client + export
- server + export
- client + server + export

# A plugins architecture

Introduced in the version 2.0, the plugins architecture will be generalized in the version 3.0. Three kinds of "plugins" are available:

- input: collect stats from the system
- output: display stats to users
- export: provide stats to others machine system

# Concerning the API

On the previous list, you can see that i only wrote "Glances server" and not Glances XML-RPC or Restful server. Glances v3 will only implement a Restful (HTTP/JSON) API (APIv3) and breaks the compatibility with the Glances v2 API.

The APIv3 should generate JSON output message as following (example for a memory GET request):

```
{
   "metadata": {"api_version": 3,
                "source": "lib",
                "plugin_name": "mem",
                "plugin_key": null
                }
   "stats": [{"available": 5071183872, "used": 3255848960, "cached": 1827352576, "percent": 39.1, "free": 5071183872, "inactive": 1388982272, "active": 3679604736, "total": 8327032832, "buffers": 477982720}],
   "views": [{"available": {'decoration': 'DEFAULT', 'optional': False, 'additional': False, 'splittable': False}, ...]
}
```

* metadata/source could be: lib (coming for a Python lib like PsUtil), snmp (from SNMP), history (from the history)
* metadata/plugin_name could be: all or a plugin name (cpu, mem, fs...)
* metadata/plugin_key could be: the key of the dict in case of the stats have many items (for example interface_name is the key of the network plugin). Default is null (None in the Python code)
* stats is a list (always, even if the list have zero or one item) of dict 
* views is a list (always, even if the list have zero or one item) of dict

_Note: the 'views' field is optional (the GET request should allow to only ask for stats and metadata)_

# Input plugins

Plugins already existing in Glances 2: system, core, ip, uptime, now, cpu, mem, memswap, load, quicklook, network, wifi, ports, diskio, fs, irq, folders, raid, sensors, docker, processcount, amps, processlist, alert

Plugins removed from Glances 2: help (why ? to many shortcuts, [a link to the official](http://glances.readthedocs.io/en/stable/cmds.html#interactive-commands) documentation will be provided). 

# Output plugins

- curses: UI for terminal and console
- api: JSON Restful API (used for example by the Web UI)
- 

# Export plugins

- CSV
- InfluxDB
- Cassandra
- CouchDB
- OpenTSDB
- Prometheus
- StatsD
- ElasticSearch
- RabbitMQ/ActiveMQ
- ZeroMQ
- Kafka
- Riemann