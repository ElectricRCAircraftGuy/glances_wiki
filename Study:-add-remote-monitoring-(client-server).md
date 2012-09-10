Following  the issue #83 (https://github.com/nicolargo/glances/issues/83)

# How to run ?

If you want to monitor the PCA from the PCB:

PCA# glances -s

PCB# glances -c @PCA

# Network

PCA listen on a TCP socket: http://docs.python.org/library/socketserver.html

PCB connects to the PCA with a TCP connection (@ and port)

The PCA:
1. build the monitoring data (with the new getAll method)
2. [serialize it using JSON](http://docs.python.org/library/json.html)
3. [compress it using the ZLIB](http://docs.python.org/library/zlib.html)
4. send it to the PCBusing the TCP connection

# User interface

The PCB @ or name is displayed in the header of the PCA Glances screen

On the PCB UI, t is possible o switch between local (PCB) and remote (PCA) view.

The PCA @ or name is displayed in the footer of the PCB Glances screen

# Todo

Change the glancesStats class and add a method (server):

    def getAll(self):
      return < All the monitoring varaible in 1 buffer >` 

On client change the display method in the glancesScreen class to manage local / remote monitoring.