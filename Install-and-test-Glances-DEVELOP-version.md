If you want to install and test the [DEVELOP](https://github.com/nicolargo/glances/tree/develop) version without deleting/uninstall your stable version, follows this procedure:

## Create a virtual environment

    pip install virtualenv
    virtualenv ~/glances-venv

## Install latest libraries

    ~/glances-venv/bin/pip install psutil

Additionaly and only on Windows operating system:

    ~/glances-venv/bin/pip install colorconsole

## Download Glances

    mkdir ~/tmp
    cd ~/tmp
    git clone -b develop git@github.com:nicolargo/glances.git

## Run the Glances HEAD version

### Standalone mode

    cd ~/tmp/glances
    LANGUAGE=en_US.utf8  ~/glances-venv/bin/python -m glances -C ~/tmp/glances/conf/glances.conf

To test the monitored processes list:

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

## How to report a bug ?

You need a GitHub account (it's free...) to log bug on the Glances' tracker.

[Click on this link](https://github.com/nicolargo/glances/issues/new) and enter the following informations:

* Glances and PsUtil version (can be retreived with the _~/glances-venv/bin/python -m glances -v_ command)
* System configuration: Operating system name and version (output of _uname -a_ and -python -V_ on GNU/Linux)
* Problem description (in English) and optionnaly error message displayed by Glances

Thks !