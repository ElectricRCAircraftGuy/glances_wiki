If you want to install and test the [DEVELOP](https://github.com/nicolargo/glances/tree/develop) branch without deleting/uninstall your stable version, you have two options:

# Use the Pypi test repository (for kids)

    pip install -i https://test.pypi.org/simple/ Glances

# Use a Python virtual environment (the easy and standard way)

## Install pre-resquisites

    pip install --user virtualenv

On Debian like system:

    apt install python-dev 

On Redhat like system

    yum install python-develop 

## Download Glances

    mkdir ~/tmp
    cd ~/tmp
    git clone -b develop https://github.com/nicolargo/glances.git
    cd ~/tmp/glances
    git checkout develop

## Create the test environment

    cd ~/tmp/glances
    make venv-python
    make venv

## Test the environment

    cd ~/tmp/glances
    make test

## Run the Glances DEVELOP version

### Standalone mode

    cd ~/tmp/glances
    make run

### Client/Server mode

Run the server (on a first terminal):

    cd ~/tmp/glances
    make run-server

And the client (on a second terminal):

    cd ~/tmp/glances
    make run-client

### Browser mode

    cd ~/tmp/glances
    make run-browser

### Webserver mode

Run the server:

    cd ~/tmp/glances
    make run-webserver

And the client in your favorite Web browser: http://@IPSERVER:61208

Where @IPSERVER is the IP address or hostname where the Glances server is running (localhost if server and client are ran on the same machine).

# How to report a bug ?

First of all, try to run Glances with the -d (Debug) flag on the command line. A glances.log file will be generated with a lot of information (to find the glances.log path, please run 'make show-version').

Then you need a GitHub account (it's free...) to log bug on the Glances' tracker.

[Click on this link](https://github.com/nicolargo/glances/issues/new) and enter the following information:

* Glances and PsUtil version (output of _make show-version_ command)
* System configuration: Operating system name and version (output of _uname -a_ and _python -V_ on GNU/Linux)
* Problem description (in English) and optionaly error message displayed by Glances
* A copy/paste of relevant messages in the log file (glances.log)
* A copy/paste of _make show-issue_

Thks !