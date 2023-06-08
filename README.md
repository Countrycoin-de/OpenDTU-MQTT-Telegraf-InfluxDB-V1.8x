# OpenDTU-MQTT-Telegraf-InfluxDB-V1.8x

Get OpenDTU topics from MQTT and imports them into InfluxDB V1.8x

This is a telegraf configuration, which collects data sent by an OpenDTU and imports it into an InfluxDB(Version 1.8x).
Because I didn't find a telegraf configuration for Influx V1.8x anywhere, I created my own.

As a template I have used the work of [smainz](https://github.com/smainz/OpenDTU-MQTT-Telegraf-influxdb-integration)  
Furthermore here is a howto from [Kraego](https://github.com/Kraego/OpenDTU-Grafana-Howto/tree/main)  
And finally the link to [OpenDTU](https://github.com/tbnobody/OpenDTU)

## Telegraf

A few explanations:

* In my telegraf configuration I use several config-files
* The main configuration is in /etc/telegraf/telegraf.conf
* All other configurations are located in the directory /etc/telegraf/telegraf.d/
* Therefore I have created my own config-file for OpenDTU -> opendtu.conf
* I also use several databases in Influx. With a 'tag' the target database is determined.  
Please note that this must be done in all other config-files as well, otherwise datasets may be written to other databases. I will publish examples for this.
* Furthermore, like  [smainz](https://github.com/smainz/OpenDTU-MQTT-Telegraf-influxdb-integration), I use environment variables.
* The file location for the environment variables is /etc/default/telegraf  
Please note that Telegraf has to be restarted when making changes to this file.

To troubleshoot problems, here are a few tips:

* A debug output can be made in the browser. 'http://<Your_telegraf_IP>:8086/debug/vars'
* In the config-file the debug output can be activated. A bit strange for me, but the debug output is then in the file /var/log/syslog  
Please be aware that the file becomes very large and uses the entire disk space if used for a long time.
