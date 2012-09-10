If you want to monitor the PCA from the PCB:

PCA# glances -s

PCB# glances -c @PCA

PCA listen on a TCP socket

PCB connects to the PCA with a TCP connection (@ and port)

The PCA build the monitoring data, encapsulate it on a JSON and them back to the PCB

The PCB @ or name is displayed in the footer of the PCA Glances screen

The PCA @ or name is displayed in the header of the PCB Glances screen