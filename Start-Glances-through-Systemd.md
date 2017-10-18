# Create unit

Create a new unit by creating a file called **glances.service** in the __/etc/systemd/system/__ folder.

## Example: start a Glances server

```
[Unit]
Description=Glances

[Service]
After=network.target
ExecStart=/usr/local/bin/glances -s
Restart=on-abort

[Install]
WantedBy=multi-user.target
```

## Example: start a Glances webserver

```
[Unit]
Description=Glances

[Service]
After=network.target
ExecStart=/usr/local/bin/glances -w
Restart=on-abort

[Install]
WantedBy=multi-user.target
```

## Example: Start a Glances client exporting stats to an InfluxDB server

```
[Unit]
Description=Glances
After=network.target influxd.service

[Service]
After=network.target
ExecStart=/usr/local/bin/glances --quiet --export-influxdb
Restart=on-failure
RestartSec=30s
TimeoutSec=30s

[Install]
WantedBy=multi-user.target
```

# Enable unit for automatic start while booting

    sudo systemctl enable glances.service

# Start the service

    sudo systemctl start glances.service

