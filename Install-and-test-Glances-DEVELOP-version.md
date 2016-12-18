If you want to install and test the [DEVELOP](https://github.com/nicolargo/glances/tree/develop) branch without deleting/uninstall your stable version, you have two options:

# Use a Python virtual environment (the easy and standard way)

## Create a virtual environment

    pip install virtualenv
    virtualenv ~/glances-venv

## Install latest libraries

    apt-get install python-dev lm-sensors 
    apt-get build-dep python-matplotlib

Note: you need to install _python-dev_ on you system before installing PSUtil (ex: apt-get install python-dev)

Note 2: if you have sensors, you should install LM-Sensors before installing P3Sensors (ex: apt-get install lm-sensors)

Note 3: If you want to install MatPlotLib, you should install the deps (ex: sudo apt-get build-dep python-matplotlib)

Install the following libs:

    ~/glances-venv/bin/pip install psutil
    ~/glances-venv/bin/pip install zeroconf
    ~/glances-venv/bin/pip install netifaces
    ~/glances-venv/bin/pip install bottle
    ~/glances-venv/bin/pip install influxdb
    ~/glances-venv/bin/pip install potsdb
    ~/glances-venv/bin/pip install statsd
    ~/glances-venv/bin/pip install pika
    ~/glances-venv/bin/pip install pystache
    ~/glances-venv/bin/pip install docker-py
    ~/glances-venv/bin/pip install py-cpuinfo
    ~/glances-venv/bin/pip install couchdb

and optionnaly:

    ~/glances-venv/bin/pip install batinfo
    ~/glances-venv/bin/pip install https://bitbucket.org/gleb_zhulik/py3sensors/get/tip.tar.gz
    ~/glances-venv/bin/pip install matplotlib

if you have a NVidia GPU add:

    ~/glances-venv/bin/pip install nvidia-ml-py

**Only on Windows** operating system:

    ~/glances-venv/bin/pip install colorconsole

## Download Glances (develop branch)

    mkdir ~/tmp
    cd ~/tmp
    git clone -b develop https://github.com/nicolargo/glances.git
    wget https://github.com/nicolargo/glances/archive/develop.zip
    unzip develop.zip 

## Run the Glances DEVELOP version

### Standalone mode

Run the CLI with the default configuration file using:

    cd ~/tmp/glances-develop
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -d -C ~/tmp/glances-develop/conf/glances.conf

### Client/Server mode

Run the server:

    cd ~/tmp/glances-develop
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -d -C ~/tmp/glances-develop/conf/glances-test.conf -s

And the client:

    cd ~/tmp/glances-develop
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -d -C ~/tmp/glances-develop/conf/glances-test.conf -c @IPSERVER

Where @IPSERVER is the IP address or hostname where the Glances server is running (localhost if server and client are ran on the same machine).

Note: if the Glances server is not running, Glances client try to fallback to SNMP server (experimental feature).

### Browser mode

Run one or more Glances servers on your LAN (or configure the list in the configuration file, [see this sample](https://github.com/nicolargo/glances/blob/develop/conf/glances-test.conf)):

    cd ~/tmp/glances-develop
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -d -C ~/tmp/glances-develop/conf/glances-test.conf --browser

### Webserver mode

Run the server:

    cd ~/tmp/glances-develop
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -d -C ~/tmp/glances-develop/conf/glances-test.conf -w

And the client in your favorite Web browser: http://@IPSERVER:61208

Where @IPSERVER is the IP address or hostname where the Glances server is running (localhost if server and client are ran on the same machine).

# How to report a bug ?

First of all, try to run Glances with the -d (Debug) flag on the command line. A /tmp/glances.log file will be generated with a lot of information.

You need a GitHub account (it's free...) to log bug on the Glances' tracker.

[Click on this link](https://github.com/nicolargo/glances/issues/new) and enter the following informations:

* Glances and PsUtil version (can be retreived with the _~/glances-venv/bin/python -m glances -V_ command)
* System configuration: Operating system name and version (output of _uname -a_ and _python -V_ on GNU/Linux)
* Problem description (in English) and optionnaly error message displayed by Glances
* A copy/paste of relevant messages in the log file (/tmp/glances.log)

Thks !