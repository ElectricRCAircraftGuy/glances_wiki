***

Test done using PSUtil 0.4.1 in the [Glances' experimental branche](https://github.com/nicolargo/glances/tree/experimental)

## CPU

> psutil.cpu_times()

> cputimes(user=92405.57, nice=467.82, system=29433.64, idle=1052180.69, iowait=10482.07, irq=6.95, softirq=378.69)

> psutil.cpu_percent()

> 16.7

_Remarks_: The statgrab Glances version use the statgrab.sg_get_cpu_percents() function

> statgrab.sg_get_cpu_percents()

> {'kernel': 1.3106160163879395, 'iowait': 2.0969855785369873, 'user': 3.2765400409698486, 'idle': 95.412841796875, 'swap': 0.0, 'time_taken': 4, 'nice': 0.0}

**=> Code needed**

**DONE IN THE EXPERIMENTAL BRANCH**

## LOAD 

No function in the psutil lib...

... but can easely replace by:

> import os

> os.getloadavg()

> (0.18, 0.16, 0.18)

> psutil.NUM_CPUS

> 2

**=> No problem**

**DONE IN THE EXPERIMENTAL BRANCH**

## MEM

> psutil.TOTAL_PHYMEM

> 2107179008L

> psutil.phymem_usage()

> usage(total=2107179008L, used=1722925056L, free=384253952L, percent=66.3)

> psutil.virtmem_usage()

> usage(total=2141188096, used=253222912, free=1887965184, percent=11.8)

**=> No problem use:**

* psutil.phymem_usage() instead of statgrab.sg_get_mem_stats()

* psutil.virtmem_usage() instead of statgrab.sg_get_swap_stats()

**DONE IN THE EXPERIMENTAL BRANCH**

## NET

> psutil.network_io_counters(True)

> {'lo': iostat(bytes_sent=932630, bytes_recv=932630, packets_sent=12035, packets_recv=12035), 'virbr0': iostat(bytes_sent=0, bytes_recv=0, packets_sent=0, packets_recv=0), 'wlan0': iostat(bytes_sent=898852414, bytes_recv=2782758847L, packets_sent=2945794, packets_recv=3282900), 'eth0': iostat(bytes_sent=200795, bytes_recv=1579873, packets_sent=2750, packets_recv=6375)}

**=> psutil.network_io_counters(True) can replace statgrab.sg_get_network_io_stats_diff() but we loose the Interface speed information of the statgrab.sg_get_network_iface_stats() function.**

**DONE IN THE EXPERIMENTAL BRANCH**

## DISK I/O

>psutil.disk_io_counters(True)

> {'sda5': iostat(read_count=125087, write_count=26136, read_bytes=624762880, write_bytes=1132367872, read_time=1796496, write_time=8928408), 'sda2': iostat(read_count=2, write_count=0, read_bytes=2048, write_bytes=0, read_time=100, write_time=0), 'sda1': iostat(read_count=454185, write_count=1733060, read_bytes=8920400896L, write_bytes=41223196672L, read_time=11263840, write_time=89853300)}

**=> No problem. psutil.disk_io_counters(True) can replace statgrab.sg_get_disk_io_stats_diff(). **

**! More detail (per logical drive) in the PsUtil function.**

**DONE IN THE EXPERIMENTAL BRANCH**

## MOUNT

> psutil.disk_partitions(True)

> [partition(device='/dev/sda1', mountpoint='/', fstype='ext4'), partition(device='proc', mountpoint='/proc', fstype='proc'), partition(device='sysfs', mountpoint='/sys', fstype='sysfs'), partition(device='fusectl', mountpoint='/sys/fs/fuse/connections', fstype='fusectl'), partition(device='', mountpoint='/sys/kernel/debug', fstype='debugfs'), partition(device='', mountpoint='/sys/kernel/security', fstype='securityfs'), partition(device='udev', mountpoint='/dev', fstype='devtmpfs'), partition(device='devpts', mountpoint='/dev/pts', fstype='devpts'), partition(device='tmpfs', mountpoint='/run', fstype='tmpfs'), partition(device='', mountpoint='/run/lock', fstype='tmpfs'), partition(device='', mountpoint='/run/shm', fstype='tmpfs'), partition(device='binfmt_misc', mountpoint='/proc/sys/fs/binfmt_misc', fstype='binfmt_misc'), partition(device='gvfs-fuse-daemon', mountpoint='/home/nicolargo/.gvfs', fstype='fuse.gvfs-fuse-daemon')]

> psutil.disk_usage('/')

> usage(total=244024213504L, used=45688664064L, free=185939759104L, percent=18.7)

**=> No problem.**

**DONE IN THE EXPERIMENTAL BRANCH**

## PROCESS

> for p in psutil.process_iter(): p.name

> 'python'

Others informations needed:

> p.name 			=> 'python'

> p.cmdline 		=> ['python', './dev/glances/src/glances.py']

> p.get_cpu_times() 	=> cputimes(user=31.21, system=55.41)

> p.get_cpu_percent(interval=0) => CPU percent since last call ([http://bit.ly/AhZVFM](http://bit.ly/AhZVFM))

> p.get_memory_info()	=> meminfo(rss=6610944, vms=13246464)

Additionnaly features:

> p.get_io_counters() 	=> io(read_count=919936045, write_count=454906, read_bytes=118784, write_bytes=0)

> p.get_memory_percent()	=> 0.3137343327216745

**=> Code needed.**

**Make try before the use of p.cmdline (raise AccessDenied(self.pid, self._process_name))**

**DONE IN THE EXPERIMENTAL BRANCH**
