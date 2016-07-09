Create a file called **glances.service** in the **/etc/systemd/system/** folder.

For example, if you want to start a Glances server, edit this file as following:

```
[Unit]
Description=Glances

[Service]
ExecStart=/usr/local/bin/glances -s
Restart=on-abort

[Install]
WantedBy=multi-user.target
```

For a Glances Web server:

```
[Unit]
Description=Glances

[Service]
ExecStart=/usr/local/bin/glances -w
Restart=on-abort

[Install]
WantedBy=multi-user.target
```

For an active client exporting stats to a InfluxDB server:

```
[Unit]
Description=Glances

[Service]
ExecStart=/usr/local/bin/glances --quiet --export-influxdb
Restart=on-abort
TimeoutStartSec=1m

[Install]
WantedBy=multi-user.target
```
