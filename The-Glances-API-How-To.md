A quick and dirty documentation for the Glances API based on XML/RPC with a 1 second cache system.

Run a Glances server:

`$ glances -s`

And play with the Python xmlrpclib (or what ever langage...), let's start:

`import xmlrpclib`

`s = xmlrpclib.ServerProxy('http://localhost:61209')`

`s.system.listMethods()`

> Get all the methods of the API

['getAll',
 'getAllLimits',
 'getAllMonitored',
 'getBatPercent',
 'getCore',
 'getCpu',
 'getDiskIO',
 'getDiskTimeSinceLastUpdate',
 'getFs',
 'getHDDTemp',
 'getLoad',
 'getMem',
 'getMemSwap',
 'getNetTimeSinceLastUpdate',
 'getNetwork',
 'getNow',
 'getProcessCount',
 'getProcessDiskTimeSinceLastUpdate',
 'getProcessList',
 'getSensors',
 'getSystem',
 'init',
 'system.listMethods',
 'system.methodHelp',
 'system.methodSignature']

`s.getAll()`

> Get all the stats in a single dict

{"load": {"min1": 0.4, "min5": 0.28, "min15": 0.34}, "process": [{"username": "root", "status": "S", "cpu_times": [0.48, 0.85], "name": "init", "memory_percent": 0.06746296564281899, "cpu_percent": 0.0, "pid": 1, "io_counters": [0, 0, 0, 0, 0], "cmdline": "/sbin/init", "memory_info": [2654208, 27807744], "time_since_update": 149.09124898910522, "nice": 0}, {"username": "root", "status": "S", "cpu_times": [0.0, 0.01], "name": "kthreadd", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 2, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "time_since_update": 149.09124898910522, "nice": 0}, {"username": "root", "status": "S", "cpu_times": [0.08, 2.3], "name": "ksoftirqd/0", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 3, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "time_since_update": 149.09124898910522, "nice": 0}, {"username": "root", "status": "S", "cpu_times": [0.0, 0.0], "name": "kworker/0:0H", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 5, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "time_since_update": 149.09124898910522, "nice": -20}, {"username": "root", "status": "S", "cpu_times": [0.0, 0.0], "name": "kworker/u:0H", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 7, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "time_since_update": 149.09124898910522, "nice": -20}, {"username": "root", "status": "S", "cpu_times": [0.05, 0.13], "name": "migration/0", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 8, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "time_since_update": 149.09124898910522, "nice": 0},...

`s.getAllLimits()`

> Get all the server's limits in a dict

{"STD": [50, 70, 90], "CPU_IOWAIT": [40.0, 60.0, 80.0], "FS": [50.0, 70.0, 90.0], "LOAD": [0.7, 1.0, 5.0], "CPU_SYSTEM": [50.0, 70.0, 90.0], "PROCESS_MEM": [50.0, 70.0, 90.0], "TEMP": [60.0, 70.0, 80.0], "MEM": [50.0, 70.0, 90.0], "CPU_USER": [50.0, 70.0, 90.0], "PROCESS_CPU": [50.0, 70.0, 90.0], "SWAP": [50.0, 70.0, 90.0], "HDDTEMP": [45, 52, 60]}

`s.getAllMonitored()`

> Get the monitored processes list in a list of dict

[{"regex": ".*stress.*", "countmin": "1", "command": "stress --version", "description": "Stress programs", "countmax": "8"}, {"regex": ".*python.*", "countmin": null, "command": null, "description": "Python programs", "countmax": null}, {"regex": ".*xeyes.*", "countmin": null, "command": null, "description": "Famous Xeyes", "countmax": null}]

_Note: new in Glances 1.7_

`s.getBatPercent()`

> Get a list of charge remaining percentages for each battery (could be more than one!)

100

_Note: new in Glances 1.7_

`s.getCore()`

> Return the number of CPU core

4

`s.getCpu()`

> Return the CPU stats in a dict

{"iowait": 0.8738048502504725, "system": 1.785601215727724, "idle": 86.58266320518352, "user": 10.643956183114177, "irq": 0.0, "nice": 0.018995757613389553}

`s.getDiskIO()`

> Return the disk IO stats in a list of dict

[{"time_since_update": 9.43163800239563, "read_bytes": 0, "write_bytes": 495616, "disk_name": "sda1"}, {"time_since_update": 9.43163800239563, "read_bytes": 0, "write_bytes": 0, "disk_name": "sda2"}, {"time_since_update": 9.43163800239563, "read_bytes": 0, "write_bytes": 0, "disk_name": "sda5"}, {"time_since_update": 9.43163800239563, "read_bytes": 0, "write_bytes": 0, "disk_name": "sr0"}]

_Note: The "time_since_update" is new in Glances 1.7_

`s.getFs()`

> Return the file systemstats in a list of dict

[{"mnt_point": "/", "used": 194091466752, "device_name": "/dev/sda1", "avail": 101005873152, "fs_type": "ext4", "size": 310896861184}, {"mnt_point": "/run", "used": 2736128, "device_name": "tmpfs", "avail": 390696960, "fs_type": "tmpfs", "size": 393433088}, {"mnt_point": "/run/rpc_pipefs", "used": 0, "device_name": "rpc_pipefs", "avail": 0, "fs_type": "rpc_pipefs", "size": 0}]

`s.getLoad()`

> Return the load stats in a dict

{"min1": 0.52, "min5": 0.54, "min15": 0.77}

`s.getMem()`

> Return the memory stats in a dict

{"inactive": 1080995840, "cached": 697253888, "used": 3033776128, "buffers": 52514816, "active": 2397990912, "total": 3934547968, "percent": 77.1, "free": 900771840}

`s.getMemSwap()`

> Return the swap memory stats in a dict

{"total": 4080005120, "percent": 15.4, "free": 3453157376, "used": 626847744}

`s.getNetwork()`

> Return the network stats in a list of dict (one item per interface)

[{"tx": 0, "cumulative_rx": 0, "rx": 0, "cumulative_cx": 0, "time_since_update": 8.817749977111816, "cx": 0, "cumulative_tx": 0, "interface_name": "eth0"}, {"tx": 1179, "cumulative_rx": 1319883, "rx": 1179, "cumulative_cx": 2639766, "time_since_update": 8.817749977111816, "cx": 2358, "cumulative_tx": 1319883, "interface_name": "lo"}, {"tx": 0, "cumulative_rx": 0, "rx": 0, "cumulative_cx": 0, "time_since_update": 8.817749977111816, "cx": 0, "cumulative_tx": 0, "interface_name": "virbr0"}, {"tx": 8420, "cumulative_rx": 219855024, "rx": 7826, "cumulative_cx": 262892076, "time_since_update": 8.817749977111816, "cx": 16246, "cumulative_tx": 43037052, "interface_name": "wlan0"}]

_Note: The "time_since_update" is new in Glances 1.7_

`s.getNow()`

> Return the current server time in a string

"19/02/2013 22:02:35"

`s.getProcessCount()`

> Return the processes summary stats in a dict

{"zombie": 2, "running": 1, "total": 222, "disk sleep": 1, "sleeping": 220}

`s.getProcessList()`

> Return the (huge) processes stats in a list of dict (one dict per processes)

[{"username": "nicolargo", "status": "S", "cpu_times": [38.16, 3.39], "name": "chromium-browse", "memory_percent": 3.9931204432566703, "cpu_percent": 7.9, "pid": 3143, "io_counters": [0, 0, 0, 0, 0], "cmdline": "/usr/lib/chromium-browser/chro", "memory_info": [157102080, 1009815552], "time_since_update": 71.5725610256195, "nice": 0}, {"username": "nicolargo", "status": "S", "cpu_times": [668.46, 88.24], "name": "gnome-shell", "memory_percent": 2.8951814993227676, "cpu_percent": 3.6, "pid": 5357, "io_counters": [237121536, 256499712, 237121536, 256499712, 1], "cmdline": "/usr/bin/gnome-shell", "memory_info": [113905664, 1924882432], "time_since_update": 71.5725610256195, "nice": 0}, {"username": "root", "status": "S", "cpu_times": [242.2, 274.7], "name": "Xorg", "memory_percent": 1.2442128123415583, "cpu_percent": 2.1, "pid": 1628, "io_counters": [0, 0, 0, 0, 0], "cmdline": "/usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none", "memory_info": [48951296, 296230912], "time_since_update": 71.5725610256195, "nice": 0}, ...

_Note: The "time_since_update" is new in Glances 1.7_

`s.getSensors()`

> Return the sensors stats in a list of dict (server should be compatible)

[{"value": 45, "label": "Core 0"}, {"value": 51, "label": "Core 2"}, {"value": 50, "label": "temp1"}, {"value": 48, "label": "temp1"}]

`s.getSystem()`

> Return the system name information in a dict

{"linux_distro": "Ubuntu 12.10", "platform": "64bit", "os_name": "Linux", "hostname": "lifebook", "os_version": "3.5.0-21-generic"}

`s.getNetTimeSinceLastUpdate()`

> Return the time since last update for the network stats

8.391342163085938

_Note: Will be depredicated in Glances 1.8 and higher, please use the time_since_update field in object data dictionaries_

`s.getDiskTimeSinceLastUpdate()`

> Return the time since last update for the disk IO stats

2.478149890899658

_Note: Will be depredicated in Glances 1.8 and higher, please use the time_since_update field in object data dictionaries_

`s.getProcessDiskTimeSinceLastUpdate()`

> Return the time since last update for the processes disk IO stats

8.696136951446533

_Note: Will be depredicated in Glances 1.8 and higher, please use the time_since_update field in object data dictionaries_