# Breaking changes

- Support fo **Python** 3.3 as been removed (yes Glances is still compatible with Python 2.7)
- Support for **PsUtil** < 5.3 as been removed
- **XML/RPC API** have changed between Glances 2 and Glances 3. It is **not** possible to use a Glances 2.x client with a Glances 3.x server and conversely
- **Restful API** upgraded to version 3 (default entry point: http://localhost:61208/api/3)

# New Features

### Add threads number in the process list #1259

A new stat is available for all displayed processes: thread count.

![](https://user-images.githubusercontent.com/776747/39767429-09a653e2-52e7-11e8-89c3-dff819bf14c6.png)

### A new way to have only REST API available and disable WEB GUI access #1149

It is now possible to run the Restful API without the Web User Interface (UI) using the --disable-webui option.

Web UI and API (default Web server mode):

```
# glances -w
Glances Web User Interface started on http://0.0.0.0:61208/
```

Web API without UI:

```
# glances -w --disable-webui
Glances Restful API Server started on http://0.0.0.0:61208/api/3/
```

### Refactor graph export plugin (& replace Matplolib by Pygal) #697

The export module has been completely refactor and the Matplotlib graph generation lib replaced by Pygal. You can generate dynamic graphs (SVG format) in a target folder. The generation starts every time the 'g' hotkey is pressed in the CLI interface or every 'generate_every' seconds (see the configuration key in the glances.conf file).

Example og graph section in the glances.conf file:

```
[graph]
# Configuration for the --export graph option
# Set the path where the graph (.svg files) will be created
# Can be overwrite by the --graph-path command line option
path=/tmp
# It is possible to generate the graphs automatically by setting the
# generate_every to a non zero value corresponding to the seconds between
# two generation. Set it to 0 to disable graph auto generation.
generate_every=60
# See followings configuration keys definitions in the Pygal lib documentation
# http://pygal.org/en/stable/documentation/index.html
width=800
height=600
style=DarkStyle
```

and run Glances with:

```
$ glances --export graph
```

Example of output (load graph)

![](https://raw.githubusercontent.com/nicolargo/glances/develop/docs/_static/graph-load.svg?sanitize=true) 

> Note: SVG files can be openned in every modern Web Browser.

### Docker module shows details about stopped containers #1152

A new configuration key has been added in the Glances configuration file (default value is False). 

Set it to True to display all the containers:

```
[docker]
# By default, Glances only display running containers
# Set the following key to True to display all containers
all=True
```

Result in the curses interface:

![](https://user-images.githubusercontent.com/776747/31486860-1c60ba06-af39-11e7-9246-6bad47946bba.png)

### Add dynamic fields in all sections of the configuration file #1204

Add the possibility to use system call in the Glances configuration file sections. 

> Note: the system call is evaluate when the Glances configuration file is read.

Example to add a tag with the hostname in an InfluxDB export section:

```
[influxdb]
prefix=`hostname`
tags=foo:bar,spam:eggs,system:`uname -a`
```

### Make plugins and export CLI option dynamical #1173

In Glances < 3.0, if you want to disable one or more plugin you should enter the following command line:

```
# glances --disable-network --disable-load
```

With Glances 3.0 and higher it is replaced by:

```
# glances --disable-plugin network,load
```

The new syntax will bring some dynamic function for the developer when a new plugin is added. 

Same kind of call should be done for the export module (--export).

A new --modules-list option should be available to display the plugins and exports module:

```
# glances --modules-list
Plugins list: load, docker, help, ip, memswap, processlist, cloud, uptime, network, percpu, irq, system, diskio, gpu, folders, core, fs, raid, mem, alert, psutilversion, hddtemp, sensors, now, quicklook, wifi, cpu, processcount, amps, batpercent, ports
Exporters list: statsd, riemann, couchdb, prometheus, rabbitmq, kafka, json, elasticsearch, influxdb, opentsdb, zeromq, csv, restful, cassandra
```

### Others news features...
- Make the left side bar width dynamic in the Curse UI #1177
-

# Bug Fixes
-

# Improvements
-
-

# Other Changes
-
-
