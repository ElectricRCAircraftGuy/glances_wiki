If you want to install and test the latest [HEAD](https://github.com/nicolargo/glances) version without deleting/uninstall your stable version, follows this procedure:

## Install latest libraries

`pip install psutil`

`pip install pysensors`

and optionnaly (if you want to test the HTML export function):

`pip install jinja2`

## Download Glances

`mkdir ~/tmp`

`cd ~/tmp`

`git clone https://github.com/nicolargo/glances.git`

## Run the Glances HEAD version

### Standalone mode

`~/tmp/glances/glances/glances.py`

or

`~/tmp/glances/glances/glances.py -e`

If you have sensors on your machine...

### Client/Server mode

On the server:

`~/tmp/glances/glances/glances.py -s`

On the client:

`~/tmp/glances/glances/glances.py -c @IPServer`

Where @IPServer is the IP address or hostname where the Glances server is running.

## Upgrade the latest HEAD version

`cd ~/tmp/glances`

`git pull master`

Enjoy...