Get with:

    p.as_dict()
    Return { 'key': value, .... }

Cpu:

    'cpu_affinity': [0, 1, 2, 3], 
    'cpu_times': cputimes(user=174.29, system=34.79),

Mem: 

    'ext_memory_info': meminfo(rss=155635712, vms=1042362368, shared=36392960, text=79446016, lib=0, data=551010304, dirty=0),

Memory mapping (list can be very long... scroll ?):

    'memory_maps': [mmap(path='/usr/lib/x86_64-linux-gnu/liblber-2.4.so.2.8.3', rss=20480, size=2154496, pss=14336, shared_clean=8192, shared_dirty=8192, private_clean=4096, private_dirty=8192, referenced=20480, anonymous=8192, swap=0), mmap(path='/var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3', rss=24576, size=24576, pss=1024, shared_clean=24576, shared_dirty=24576, private_clean=0, private_dirty=0, referenced=24576, anonymous=0, swap=0), ... ],

Connections:

    'connections': [],

File descriptors:

    'num_fds': 34,

Open files:

    'open_files': [openfile(path='/home/nicolargo/.xsession-errors', fd=2), openfile(path='/home/nicolargo/.mozilla/firefox/zbgzu717.default/cert8.db', fd=22), ... ]

Number of threads:

    'num_threads': 19,

