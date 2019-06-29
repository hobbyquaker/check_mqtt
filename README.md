# check_mqtt 1.0

[![License][mit-badge]][mit-url]

> Dead simple Nagios/Icinga Plugin for checking MQTT pub/sub

Dead simple Bash script that checks if a published message gets received by a subscription. Depends on `mosquitto_pub` and `mosquitto_sub`.

### Install

Place the file `check_mqtt` somewhere (e.g. `/usr/local/bin/`) and make it executable.


### Usage

Use the same command line arguments as with the `mosquitto_sub` command. 


### Nagios command and service definition example

```
define command {
        command_name    check_mqtt
        command_line    /usr/local/bin/check_mqtt.sh -h 192.168.1.100 -p 8883 -u user -P password -t nagios/check --cafile /etc/ssl/certs/DST_Root_CA_X3.pem
}

define service {
        use                     generic-service
        host_name               servername
        service_description     MQTT Pub/Sub
        check_command           check_mqtt
}
```

## License

MIT (c) 2018, 2019 [Sebastian Raff](https://github.com/hobbyquaker)

[mit-badge]: https://img.shields.io/badge/License-MIT-blue.svg?style=flat
[mit-url]: LICENSE
