Following  the issue #83 (https://github.com/nicolargo/glances/issues/83)

# How to run ?

If you want to monitor the PCA from the PCB:

PCA# glances -s

PCB# glances -c @PCA

# Network

PCA listen on a TCP socket

PCB connects to the PCA with a TCP connection (@ and port)

The PCA build the monitoring data, encapsulate it on a JSON and send its to the PCB

# User interface

The PCB @ or name is displayed in the footer of the PCA Glances screen

The PCA @ or name is displayed in the header of the PCB Glances screen

# Todo

Change the glancesStats class and add a method:

def getAll(self):
  return < All the monitoring varaible in 1 buffer >

