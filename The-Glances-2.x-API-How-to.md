**Only for Glances v2.x !**

Glances API is based on a **XMLRPC server**.

Server side
===========

    $ glances -s

    Glances server is running on 0.0.0.0:61209

By default, Glances server listens to the TCP port 61209. You can change it using the -p <port> option.

Client side
===========

Implementation example using the Python xmlrpclib:

Connect to the XMLRPC server:

    In [1]: import xmlrpclib

    In [2]: s = xmlrpclib.ServerProxy('http://localhost:61209')


List all the availables plugins on the server side:

    In [5]: s.getAllPlugins()

    Out[5]: '["load", "help", "memswap", "processlist", "uptime", "monitor", "percpu", "system", "diskio", "core", "fs", "mem", "alert", "psutilversion", "hddtemp", "sensors", "now", "network", "allmoni.__repr__", "processcount", "batpercent", "cpu"]'

Get all the stats in a single dictionnary:

    In [8]: s.getAll()

Out[8]: '{"load": {"cpucore": 4, "min1": 0.17, "min5": 0.37, "min15": 0.44}, "core": {"phys": 1, "log": 4}, "uptime": "8 days, 20:51:07", "fs": [{"mnt_point": "/", "used": 84199976960, "percent": 34.6, "device_name": "/dev/sda2", "fs_type": "ext4", "size": 243020783616}, {"mnt_point": "/boot/efi", "used": 3510272, "percent": 0.7, "device_name": "/dev/sda1", "fs_type": "vfat", "size": 535805952}], "monitor": [{"regex": ".*python.*", "count": 6, "description": "Python programs", "countmin": null, "command": null, "result": "CPU: 1.3% | MEM: 6.1%", "countmax": null}, {"regex": ".*xeyes.*", "count": 0, "description": "Famous Xeyes", "countmin": "1", "command": null, "result": "CPU: 0.0% | MEM: 0.0%", "countmax": null}], "percpu": [{"softirq": 0.0, "iowait": 0.3529731197397322, "system": 2.905240293241723, "idle": 92.94053760534734, "user": 3.7740972033720044, "irq": 0.027151778441532704, "steal": 0.0, "nice": 0.0}, {"softirq": 0.0, "iowait": 0.2436383324309774, "system": 1.570113697888942, "idle": 95.10016242555862, "user": 3.059014618297888, "irq": 0.027070925825678046, "steal": 0.0, "nice": 0.0}, {"softirq": 0.0, "iowait": 0.13542795232936913, "system": 1.4084507042253696, "idle": 94.63705308776072, "user": 3.7919826652237596, "irq": 0.027085590465868052, "steal": 0.0, "nice": 0.0}, {"softirq": 0.0, "iowait": 0.24363833243095337, "system": 0.7309149972928121, "idle": 95.45208446128068, "user": 3.573362208986534, "irq": 0.0, "steal": 0.0, "nice": 0.0}], "mem": {"available": 5270933504, "used": 3002662912, "cached": 2955857920, "percent": 36.3, "free": 5270933504, "inactive": 2042101760, "active": 3487334400, "total": 8273596416, "buffers": 178614272}, "sensors": [{"type": "temperature_core", "value": 27, "label": "temp1"}, {"type": "temperature_core", "value": 29, "label": "temp2"}, {"type": "temperature_core", "value": 58, "label": "Physical id 0"}, {"type": "temperature_core", "value": 56, "label": "Core 0"}, {"type": "temperature_core", "value": 59, "label": "Core 1"}, {"type": "battery", "value": 73, "label": "Battery (%)"}], "system": {"linux_distro": "Ubuntu 14.04", "platform": "64bit", "os_name": "Linux", "hostname": "xps", "os_version": "3.13.0-24-generic"}, "alert": [], "psutilversion": [2, 1, 0], "memswap": {"used": 41889792, "percent": 0.5, "free": 8448425984, "sout": 61145088, "total": 8490315776, "sin": 5386240}, "diskio": [{"time_since_update": 37.00421190261841, "read_bytes": 851968, "write_bytes": 2134016, "disk_name": "sda2"}, {"time_since_update": 37.00421190261841, "read_bytes": 0, "write_bytes": 0, "disk_name": "sda3"}, {"time_since_update": 37.00421190261841, "read_bytes": 0, "write_bytes": 0, "disk_name": "sda1"}], "hddtemp": [], "processcount": {"zombie": 2, "running": 1, "total": 227, "thread": 567, "sleeping": 225}, "batpercent": [{"value": 73, "label": "Battery (%)"}], "now": "2014-05-30 18:11:58", "processlist": [{"username": "root", "status": "S", "cpu_times": [4.36, 2.47], "name": "init", "memory_percent": 0.0819338974147999, "cpu_percent": 0.0, "pid": 1, "io_counters": [0, 0, 0, 0, 0], "cmdline": "/sbin/init", "memory_info": [6778880, 38236160], "time_since_update": 37.004262924194336, "nice": 0}, {"username": "root", "status": "S", "cpu_times": [0.0, 0.08], "name": "kthreadd", "memory_percent": 0.0, "cpu_percent": 0.0, "pid": 2, "io_counters": [0, 0, 0, 0, 0], "cmdline": "", "memory_info": [0, 0], "time_since_update": 37.004262924194336, "nice": 0}, ... ], "cpu": {"softirq": 0.0, "iowait": 0.2, "system": 1.7, "guest": 0.0, "idle": 94.5, "user": 3.5, "guest_nice": 0.0, "irq": 0.0, "steal": 0.0, "nice": 0.0}, "network": [{"tx": 15688, "cumulative_rx": 164472551, "rx": 15688, "cumulative_cx": 328945102, "time_since_update": 37.02545785903931, "cx": 31376, "cumulative_tx": 164472551, "interface_name": "lo"}, {"tx": 0, "cumulative_rx": 5180644, "rx": 0, "cumulative_cx": 231328829, "time_since_update": 37.02545785903931, "cx": 0, "cumulative_tx": 226148185, "interface_name": "docker0"}, {"tx": 21124, "cumulative_rx": 6809114787, "rx": 24104, "cumulative_cx": 10178000057, "time_since_update": 37.02545785903931, "cx": 45228, "cumulative_tx": 3368885270, "interface_name": "wlan0"}], "help": null}'

Get all the limits set by the server:

    In [9]: s.getAllLimits()

Out[9]: '{u'load': {u'load_critical': 5.0, u'load_careful': 0.7, u'load_warning': 1.0}, u'help': {}, u'memswap': {u'memswap_careful': 50.0, u'memswap_critical': 90.0, u'memswap_warning': 70.0}, u'processlist': {u'processlist_cpu_critical': 90.0, u'processlist_cpu_warning': 70.0, u'processlist_mem_critical': 90.0, u'processlist_mem_warning': 70.0, u'processlist_mem_careful': 50.0, u'processlist_cpu_careful': 50.0}, u'uptime': {}, u'monitor': {}, u'percpu': {u'percpu_system_warning': 70.0, u'percpu_user_critical': 90.0, u'percpu_user_careful': 50.0, u'percpu_system_careful': 50.0, u'percpu_iowait_careful': 50.0, u'percpu_iowait_critical': 90.0, u'percpu_system_critical': 90.0, u'percpu_iowait_warning': 70.0, u'percpu_user_warning': 70.0}, u'system': {}, u'diskio': {}, u'core': {}, u'fs': {u'fs_careful': 50.0, u'fs_critical': 90.0, u'fs_warning': 70.0}, u'raid': {}, u'mem': {u'mem_careful': 50.0, u'mem_warning': 70.0, u'mem_critical': 90.0}, u'alert': {}, u'psutilversion': {}, u'hddtemp': {}, u'sensors': {u'sensors_temperature_hdd_critical': 60.0, u'sensors_temperature_hdd_warning': 52.0, u'sensors_temperature_core_careful': 60.0, u'sensors_temperature_core_critical': 80.0, u'sensors_temperature_core_warning': 70.0, u'sensors_battery_careful': 80.0, u'sensors_temperature_hdd_careful': 45.0, u'sensors_battery_warning': 90.0, u'sensors_battery_critical': 95.0}, u'now': {}, u'docker': {}, u'network': {}, u'processcount': {}, u'batpercent': {}, u'cpu': {u'cpu_user_careful': 50.0, u'cpu_user_critical': 90.0, u'cpu_system_careful': 50.0, u'cpu_user_warning': 70.0, u'cpu_steal_critical': 90.0, u'cpu_iowait_warning': 70.0, u'cpu_system_critical': 90.0, u'cpu_system_warning': 70.0, u'cpu_iowait_careful': 50.0, u'cpu_steal_careful': 50.0, u'cpu_steal_warning': 70.0, u'cpu_iowait_critical': 90.0}}'

Get all the plugins views (usefull to display stats with alert):

    In [9]: s.getAllViews()

Out[9]: '{u'load': {u'cpucore': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'min1': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'min5': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'min15': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}}, u'help': {}, u'memswap': {u'used': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}, u'percent': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'free': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'sout': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'total': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'sin': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'processlist': {}, u'uptime': {}, u'monitor': {}, u'percpu': {}, u'system': {}, u'diskio': {u'sda2': {u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'time_since_update': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'read_bytes': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'write_bytes': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'disk_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'sda3': {u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'time_since_update': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'read_bytes': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'write_bytes': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'disk_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'sda1': {u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'time_since_update': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'read_bytes': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'write_bytes': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'disk_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}}, u'core': {}, u'fs': {u'/boot/efi': {u'mnt_point': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'used': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'percent': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'free': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'device_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'fs_type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'size': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'/': {u'mnt_point': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'used': {u'decoration': u'CAREFUL', u'optional': False, u'additional': False, u'splittable': False}, u'percent': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'free': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'device_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'fs_type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'size': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}}, u'raid': {}, u'mem': {u'available': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'used': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}, u'cached': {u'decoration': u'DEFAULT', u'optional': True, u'additional': False, u'splittable': False}, u'percent': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'free': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'inactive': {u'decoration': u'DEFAULT', u'optional': True, u'additional': False, u'splittable': False}, u'active': {u'decoration': u'DEFAULT', u'optional': True, u'additional': False, u'splittable': False}, u'total': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'buffers': {u'decoration': u'DEFAULT', u'optional': True, u'additional': False, u'splittable': False}}, u'alert': {}, u'psutilversion': {}, u'hddtemp': {}, u'sensors': {u'Physical id 0': {u'type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'value': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'label': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'temp2': {u'type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'value': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'label': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'temp1': {u'type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'value': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'label': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'Core 1': {u'type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'value': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'label': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'Core 0': {u'type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'value': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'label': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'Battery (%)': {u'type': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'value': {u'decoration': u'OK', u'optional': False, u'additional': False, u'splittable': False}, u'label': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}}, u'now': {}, u'docker': {}, u'network': {u'lo': {u'tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'time_since_update': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'interface_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'veth374f': {u'tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'time_since_update': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'interface_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'wlan0': {u'tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'time_since_update': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'interface_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}, u'docker0': {u'tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'rx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'time_since_update': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'cumulative_tx': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'key': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'interface_name': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}}}, u'processcount': {}, u'batpercent': {}, u'cpu': {u'softirq': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'iowait': {u'decoration': u'OK_LOG', u'optional': True, u'additional': False, u'splittable': False}, u'system': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}, u'guest': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'idle': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'user': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}, u'guest_nice': {u'decoration': u'DEFAULT', u'optional': False, u'additional': False, u'splittable': False}, u'irq': {u'decoration': u'DEFAULT', u'optional': True, u'additional': False, u'splittable': False}, u'total': {u'decoration': u'OK_LOG', u'optional': False, u'additional': False, u'splittable': False}, u'steal': {u'decoration': u'OK', u'optional': True, u'additional': False, u'splittable': False}, u'nice': {u'decoration': u'DEFAULT', u'optional': True, u'additional': False, u'splittable': False}}}'

Get the monitored process list

    In [13]: s.getAllMonitored()

Out[13]: '[{"regex": ".*python.*", "count": 6, "description": "Python programs", "countmin": null, "command": null, "result": "CPU: 5.3% | MEM: 6.1%", "countmax": null}, {"regex": ".*xeyes.*", "count": 0, "description": "Famous Xeyes", "countmin": "1", "command": null, "result": "CPU: 0.0% | MEM: 0.0%", "countmax": null}]'

Get system information:

    In [32]: s.getSystem()

Out[32]: '{"linux_distro": "Ubuntu 14.04", "platform": "64bit", "os_name": "Linux", "hostname": "xps", "os_version": "3.13.0-24-generic"}'

Get CPU stats

    In [34]: s.getCpu()

Out[34]: '{"softirq": 0.0, "iowait": 0.1, "system": 1.1, "guest": 0.0, "idle": 96.4, "user": 2.3, "guest_nice": 0.0, "irq": 0.0, "steal": 0.0, "nice": 0.0}'

Get CPU stats (per CPU core)

    In [35]: s.getPerCpu()

Out[35]: '[{"softirq": 0.0, "iowait": 0.0, "system": 1.570680628271919, "idle": 96.1605584642101, "user": 2.2687609075021196, "irq": 0.0, "steal": 0.0, "nice": 0.0}, {"softirq": 0.0, "iowait": 0.0, "system": 1.9130434782591295, "idle": 94.95652173913106, "user": 3.130434782613757, "irq": 0.0, "steal": 0.0, "nice": 0.0}, {"softirq": 0.0, "iowait": 0.173913043478261, "system": 0.8695652173944678, "idle": 96.6956521739121, "user": 2.260869565219289, "irq": 0.0, "steal": 0.0, "nice": 0.0}, {"softirq": 0.0, "iowait": 0.0, "system": 0.6956521739126309, "idle": 97.73913043481163, "user": 1.3913043478252618, "irq": 0.0, "steal": 0.0, "nice": 0.17391304347840486}]'

Get the number of physival and logical core:

    In [36]: s.getCore()

Out[36]: '{"phys": 1, "log": 4}'

Get load stats:

    In [37]: s.getLoad()

Out[37]: '{"cpucore": 4, "min1": 0.05, "min5": 0.14, "min15": 0.22}'

Get mem (aka RAM) stats:

    In [38]: s.getMem()

Out[38]: '{"available": 5266268160, "used": 3007328256, "cached": 2949533696, "percent": 36.3, "free": 5266268160, "inactive": 2034712576, "active": 3497422848, "total": 8273596416, "buffers": 183599104}'

Get swap stats:

    In [39]: s.getMemSwap()

Out[39]: '{"used": 41881600, "percent": 0.5, "free": 8448434176, "sout": 61145088, "total": 8490315776, "sin": 5455872}'

Get network interfaces stats

    In [48]: s.getNetwork()

Out[48]: '[{"tx": 750, "cumulative_rx": 164699607, "rx": 750, "cumulative_cx": 329399214, "time_since_update": 1, "cx": 1500, "cumulative_tx": 164699607, "interface_name": "lo"}, {"tx": 0, "cumulative_rx": 5180644, "rx": 0, "cumulative_cx": 231328829, "time_since_update": 1, "cx": 0, "cumulative_tx": 226148185, "interface_name": "docker0"}, {"tx": 398, "cumulative_rx": 6813463626, "rx": 245, "cumulative_cx": 10184194830, "time_since_update": 1, "cx": 643, "cumulative_tx": 3370731204, "interface_name": "wlan0"}]'

Get disk IO stats:

    In [49]: s.getDiskIO()

Out[49]: '[{"time_since_update": 21.43511390686035, "read_bytes": 0, "write_bytes": 475136, "disk_name": "sda2"}, {"time_since_update": 21.43511390686035, "read_bytes": 0, "write_bytes": 0, "disk_name": "sda3"}, {"time_since_update": 21.43511390686035, "read_bytes": 0, "write_bytes": 0, "disk_name": "sda1"}]'

Get file system stats:

    In [50]: s.getFs()

Out[50]: '[{"mnt_point": "/", "used": 84199280640, "percent": 34.6, "device_name": "/dev/sda2", "fs_type": "ext4", "size": 243020783616}, {"mnt_point": "/boot/efi", "used": 3510272, "percent": 0.7, "device_name": "/dev/sda1", "fs_type": "vfat", "size": 535805952}]'

Get sensors stats:

    In [51]: s.getSensors()

Out[51]: '[{"type": "temperature_core", "value": 27, "label": "temp1"}, {"type": "temperature_core", "value": 29, "label": "temp2"}, {"type": "temperature_core", "value": 55, "label": "Physical id 0"}, {"type": "temperature_core", "value": 54, "label": "Core 0"}, {"type": "temperature_core", "value": 55, "label": "Core 1"}, {"type": "battery", "value": 66, "label": "Battery (%)"}]'

Get processes summary:
 
    In [52]: s.getProcessCount()

Out[52]: '{"zombie": 2, "running": 1, "total": 228, "thread": 569, "sleeping": 226}'

Get monitored system stats:

    In [53]: s.getMonitor()

Out[53]: '[{"regex": ".*python.*", "count": 6, "description": "Python programs", "countmin": null, "command": null, "result": "CPU: 1.8% | MEM: 6.2%", "countmax": null}, {"regex": ".*xeyes.*", "count": 0, "description": "Famous Xeyes", "countmin": "1", "command": null, "result": "CPU: 0.0% | MEM: 0.0%", "countmax": null}]'

Get full processlist:

    In [54]: s.getProcessList()

Out[54]: '[{"username": "root", "status": "S", "cpu_times": [4.4, 2.49], "name": "init", "memory_percent": 0.0819338974147999, "cpu_percent": 0.0, "pid": 1, "io_counters": [0, 0, 0, 0, 0], "cmdline": "/sbin/init", "memory_info": [6778880, 38236160], "time_since_update": 20.550407886505127, "nice": 0}, ... ]

Get server date:

    In [55]: s.getNow()

Out[55]: '"2014-05-30 21:34:53"'

Get server uptime:

    In [56]: s.getUptime()

Out[56]: '"9 days, 0:14:21"'

Get server PsUtil version number:

    In [59]: s.getPsUtilVersion()

Out[59]: '[2, 1, 0]'
