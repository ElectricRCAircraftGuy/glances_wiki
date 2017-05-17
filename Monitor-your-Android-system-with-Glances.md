Glances can be installed on your **rooted** Android system and used to monitor locally or remotely your device.

# Install Glances on your Android device

Please follow [this procedure](https://github.com/nicolargo/glances/tree/develop#android).

> You need a **rooted** Android system to use Glances.

# Monitor locally your Android device

Start the Temux application and enter the following command line:

`$ glances`

If you want to stop the process, please have a long click on the screen then More... > Kill process.

# Monitor remotely your Android device

### From a GNU/Linux or MacOS terminal

First of all install Glances on you GNU/Linux or MacOS. 

On your Android, start the Temux application and enter the command line: 

`$ ifconfig`

Found your local IP address (probably the wlan0 one), then start Glances in server mode (-s):

`$ glances -s`

On your GNU/Linux or MacOS, enter the command line in a terminal:

`$ glances -c <@ip android device>`

And here it is:

![Android Glances](http://pix.toile-libre.org/upload/original/1494925754.png)

### From a Web browser

On your Android, start the Temux application and enter the command line: 

`$ ifconfig`

Found your local IP address (probably the wlan0 one), then start Glances in Web server mode (-w):

`$ glances -w`

On your Windows, GNU/Linux or MacOS, start your Web browser and enter the following URL:

`<@ip android device>:61208`
