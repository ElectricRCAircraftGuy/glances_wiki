If you want to install and test the [DEVELOP](https://github.com/nicolargo/glances/tree/develop) version without deleting/uninstall your stable version, follows this procedure:

## Create a virtual environment

    pip install virtualenv
    virtualenv ~/glances-venv

## Install latest libraries

Note: you need to install _python-dev_ on you system before installing PSUtil (ex: apt-get install python-dev)

Note 2: if you have sensors, you should install LM-Sensors before installing P3Sensors (ex: apt-get install lm-sensors)

Install the following libs:

    ~/glances-venv/bin/pip install psutil
    ~/glances-venv/bin/pip install bottle
    ~/glances-venv/bin/pip install batinfo
    ~/glances-venv/bin/pip install https://bitbucket.org/gleb_zhulik/py3sensors/get/tip.tar.gz

Additionaly and **only on Windows** operating system:

    ~/glances-venv/bin/pip install colorconsole

## Download Glances (develop branch)

    mkdir ~/tmp
    cd ~/tmp
    git clone -b develop https://github.com/nicolargo/glances.git

## Run the Glances DEVELOP version

### Standalone mode

Run the CLI with the default configuration file using:

    cd ~/tmp/glances
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -C ~/tmp/glances/conf/glances.conf

To test the monitored processes list configuration file:

    cd ~/tmp/glances
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -C ~/tmp/glances/conf/glances-monitor.conf

### Client/Server mode

Run the server:

    cd ~/tmp/glances
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -C ~/tmp/glances/conf/glances-monitor.conf -s

And the client:

    cd ~/tmp/glances
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -C ~/tmp/glances/conf/glances-monitor.conf -c @IPSERVER

Where @IPSERVER is the IP address or hostname where the Glances server is running (localhost if server and client are ran on the same machine).

Note: if the Glances server is not running, Glances client try to fallback to SNMP server (early experimental function).

### Webserver mode

Run the server:

    cd ~/tmp/glances
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -C ~/tmp/glances/conf/glances-monitor.conf -w

And the client in your favorite Web browser: http://@IPSERVER:61208

Where @IPSERVER is the IP address or hostname where the Glances server is running (localhost if server and client are ran on the same machine).

## How to report a bug ?

You need a GitHub account (it's free...) to log bug on the Glances' tracker.

[Click on this link](https://github.com/nicolargo/glances/issues/new) and enter the following informations:

* Glances and PsUtil version (can be retreived with the _~/glances-venv/bin/python -m glances -V_ command)
* System configuration: Operating system name and version (output of _uname -a_ and _python -V_ on GNU/Linux)
* Problem description (in English) and optionnaly error message displayed by Glances

Thks !