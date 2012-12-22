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

`~/tmp/glances/glances/glances.py`

Enjoy...