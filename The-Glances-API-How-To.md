A quick and dirty documentation for the Glances API based on XML/RPC with a 1 second cache system.

Run a Glances server:

`$ glances -s`

And play with the Python xmlrpclib (or what ever langage...), let's start:

`import xmlrpclib`

`s = xmlrpclib.ServerProxy('http://localhost:61209')`

`s.system.listMethods()`

['getAll',
 'getAllLimits',
 'getCore',
 'getCpu',
 'getDiskIO',
 'getFs',
 'getLoad',
 'getMem',
 'getMemSwap',
 'getNetwork',
 'getNow',
 'getProcessCount',
 'getProcessList',
 'getSensors',
 'getSystem',
 'init',
 'system.listMethods',
 'system.methodHelp',
 'system.methodSignature']

`s.getAll()`

{"load": {"min1": 0.3, "min5": 0.7, "min15": 1.03}, "process": [{"username": "root", "status": "S", "cpu_times": [1.93, 1.26], "name": "init", "memory_percent": 0.057985619150037006, "cpu_percent": 0.0, "pid": 1, "io_counters": [0, 0, 0, 0, 0], "cmdline": "/sbin/init", "memory_info": [2281472, 25194496], "nice": 0}, {"username": "root", "status": "S", "cpu_times": [0.0, 0.14], "name": "kthreadd", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 2, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "nice": 0}, {"username": "root", "status": "S", "cpu_times": [0.0, 36.07], "name": "ksoftirqd/0", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 3, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "nice": 0}, {"username": "root", "status": "S", "cpu_times": [0.0, 1.58], "name": "migration/0", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 6, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "nice": 0}, {"username": "root", "status": "S",...

`s.getAllLimits()`

{"STD": [50, 70, 90], "CPU_IOWAIT": [40, 60, 80], "FS": [50, 70, 90], "LOAD": [0.7, 1.0, 5.0], "CPU_SYSTEM": [50, 70, 90], "PROCESS_MEM": [50, 70, 90], "TEMP": [60, 70, 80], "MEM": [50, 70, 90], "CPU_USER": [50, 70, 90], "PROCESS_CPU": [50, 70, 90], "SWAP": [50, 70, 90]}

`s.getCore()`

4

`s.getCpu()`

{"iowait": 0.8738048502504725, "system": 1.785601215727724, "idle": 86.58266320518352, "user": 10.643956183114177, "irq": 0.0, "nice": 0.018995757613389553}

`s.getDiskIO()`

[{"read_bytes": 8192, "write_bytes": 2703360, "disk_name": "sda1"}, {"read_bytes": 0, "write_bytes": 0, "disk_name": "sda2"}, {"read_bytes": 4096, "write_bytes": 0, "disk_name": "sda5"}, {"read_bytes": 0, "write_bytes": 0, "disk_name": "sr0"}]

`s.getFs()`

[{"mnt_point": "/", "used": 102535917568, "device_name": "/dev/sda1", "avail": 192695640064, "fs_type": "ext4", "size": 311031078912}, {"mnt_point": "/run", "used": 995328, "device_name": "tmpfs", "avail": 785915904, "fs_type": "tmpfs", "size": 786911232}]

`s.getLoad()`

{"min1": 0.52, "min5": 0.54, "min15": 0.77}

`s.getMem()`

{"inactive": 1080995840, "cached": 697253888, "used": 3033776128, "buffers": 52514816, "active": 2397990912, "total": 3934547968, "percent": 77.1, "free": 900771840}

`s.getMemSwap()`

{"total": 4080005120, "percent": 15.4, "free": 3453157376, "used": 626847744}

`s.getNetwork()`

[{"interface_name": "eth0", "rx": 0, "tx": 0}, {"interface_name": "lo", "rx": 3829, "tx": 3829}, {"interface_name": "virbr0", "rx": 0, "tx": 0}, {"interface_name": "wlan0", "rx": 32186, "tx": 29183}]

`s.getNow()`

"19/02/2013 22:02:35"

`s.getProcessCount()`

{"zombie": 2, "running": 1, "total": 222, "disk sleep": 1, "sleeping": 220}

`s.getProcessList()`

[{"username": "nicolargo", "status": "S", "cpu_times": [9563.32, 1604.89], "name": "chromium-browser", "memory_percent": 7.668155692948969, "cpu_percent": 1.8, "pid": 7063, "io_counters": [2825959424, 12815888384, 2825959424, 12815646720, 1], "cmdline": "chromium-browser", "memory_info": [301707264, 1122258944], "nice": 0}, {"username": "nicolargo", "status": "S", "cpu_times": [310.4, 13.31], "name": "chromium-browse", "memory_percent": 6.856981645521522, "cpu_percent": 0.2, "pid": 23242, "io_counters": [0, 0, 0, 0, 0], "cmdline": "/usr/lib/chromium-browser/chro", "memory_info": [269791232, 1139535872], "nice": 0}, {"username": "nicolargo", "status": "S", "cpu_times": [432.06, 60.84]...

`s.getSensors()`

[{"value": 45, "label": "Core 0"}, {"value": 51, "label": "Core 2"}, {"value": 50, "label": "temp1"}, {"value": 48, "label": "temp1"}]

`s.getSystem()`

{"linux_distro": "Ubuntu 12.10", "platform": "64bit", "os_name": "Linux", "hostname": "lifebook", "os_version": "3.5.0-21-generic"}
