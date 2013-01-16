If you want to install and test the latest [HEAD](https://github.com/nicolargo/glances) version without deleting/uninstall your stable version, follows this procedure:

## Install latest libraries

    pip install psutil
    pip install pysensors

and optionnaly (if you want to test the HTML export function):

    pip install jinja2

## Download Glances

    mkdir ~/tmp
    cd ~/tmp
    git clone https://github.com/nicolargo/glances.git

## Run the Glances HEAD version

### Standalone mode

    ~/tmp/glances/glances/glances.py

or if you have sensors (lm-sensors) on your machine:

    ~/tmp/glances/glances/glances.py -e

### Client/Server mode

On the server:

    ~/tmp/glances/glances/glances.py -s

On the client:

    ~/tmp/glances/glances/glances.py -c @IPServer

Where @IPServer is the IP address or hostname where the Glances server is running.

## Upgrade the latest HEAD version

    cd ~/tmp/glances
    git pull master

## How to report a bug ?

You need a GitHub account (it's free...) to log bug on the Glances' tracker.

[Click on this link](https://github.com/nicolargo/glances/issues/new) and enter the following informations:

* Glances and PsUtil version (can be retreived with the _~/tmp/glances/glances/glances.py -v_ command)
* System configuration: Operating system name and version (output of _uname -a_ on GNU/Linux)
* Output of the unitary test (_~/tmp/glances/glances/unitest.py_)
* Problem description (in English) and optionnaly error message displayed by Glances

Thks !