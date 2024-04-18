# autobahn-mqtt
This is a public repository that provides some examples and guidelines of MQTT

## How to run MQTT server on my mac (Mosquitto)

### Commands

[🔗 reference](https://gist.github.com/KazChe/6bcafbaf29e10a7f309d3ca2e2a0f706)

```bash
# Installs Mosquitto
$ brew install mosquitto

# Links to the installed version of mosquitto
$ brew link mosquitto

# Start Mosquitto
$ brew services start mosquitto

# Stop Mosquitto
$ brew services stop mosquitto

# Subscribes to the topic (h: host, p: port:  t: topic)
$ mosquitto_sub -h 127.0.0.1 -p 1883 -t topic

# Publishes the message (m: message)
$ mosquitto_pub -h 127.0.0.1 -p 1883 -t topic -m "test message"

# For more information...
$ mosquitto_sub --help
$ mosquitto_pub --help
```


### Results
- iOS Sample App: [EmCuTeeTee](https://github.com/adam-fowler/EmCuTeeTee)

| Pub/Sub | After stop mosquitto |
| --- | --- |
| <img width="1142" alt="스크린샷 2024-04-18 오후 10 02 31" src="https://github.com/autobahn-no3/autobahn-research-mqtt/assets/53814741/b292347c-6c6a-4aa0-bf49-f645570dd692"> | <img width="1127" alt="스크린샷 2024-04-18 오후 10 03 04" src="https://github.com/autobahn-no3/autobahn-research-mqtt/assets/53814741/5b653bfb-1365-419c-95e9-cd4a1b86972c"> |
