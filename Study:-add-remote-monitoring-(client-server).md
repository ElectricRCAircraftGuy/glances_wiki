Following  the issue #83 (https://github.com/nicolargo/glances/issues/83)

# How to run ?

If you want to monitor the PCA from the PCB:

PCA# glances -s

PCB# glances -c @PCA

# Network

PCA listen on a TCP socket: http://docs.python.org/library/socketserver.html

PCB connects to the PCA with a TCP connection (@ and port)

The PCA build the monitoring data, serialize it using JSON and send it to the PCB

# User interface

The PCB @ or name is displayed in the header of the PCA Glances screen

On the PCB UI, t is possible o switch between local (PCB) and remote (PCA) view.

The PCA @ or name is displayed in the footer of the PCB Glances screen

# Todo

Change the glancesStats class and add a method (server):

    def getAll(self):
      return < All the monitoring varaible in 1 buffer >` 

On client change the display method in the glancesScreen class to manage local / remote monitoring.