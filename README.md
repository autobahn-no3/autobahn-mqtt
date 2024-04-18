# MQTT for Apple Platforms | autobahn-no3

This is a public repository that provides some examples and guidelines of MQTT(especially, MQTT NIO) for Apple platforms (iOS, macOS)

## Overview

<img width="788" alt="스크린샷 2024-04-18 오후 10 18 33" src="https://github.com/autobahn-no3/autobahn-mqtt/assets/53814741/3ddec62d-594b-4e8c-a748-e09b16caf6a0">


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

## Connections

### NIO Transport Services

On macOS and iOS you can use the *NIO Transport Services library (NIOTS)* and *Apple’s Network.framework* for communication with the *MQTT broker*. (default)

| | NIOSSL | NIOTS |
| --- | --- | --- |
| EventLoopGroup | `MultiThreadedEventLoopGroup` | `NIOTSEventLoopGroup` |
| TLSConfiguration | `NIOSSL.TLSConfiguration` | `TSTLSConfiguration` |

If you provide a `MultiThreadedEventLoopGroup` and a `TSTLSConfiguration` then the client will throw an error. If you are running on *iOS* you should *always choose NIOTS*.[^1](https://swift-server-community.github.io/mqtt-nio/documentation/mqttnio/mqttnio-connections#NIO-Transport-Services)
