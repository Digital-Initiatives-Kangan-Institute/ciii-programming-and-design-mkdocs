# MQTT Overview

MQTT (Message Queuing Telemetry Transport) is a lightweight messaging protocol designed for devices with limited bandwidth. It uses a publish/subscribe model where clients send and receive messages through a central broker.

---

## How MQTT Works

MQTT uses three key concepts:

- **Broker** — a server that manages message delivery between clients
- **Publisher** — a client that sends messages to a topic on the broker
- **Subscriber** — a client that listens for messages on a topic

```
Publisher  --->  [Broker]  --->  Subscriber
                    |
                    +--------->  Subscriber
```

When a publisher sends a message to a topic, the broker forwards it to every client subscribed to that topic. Publishers and subscribers never communicate directly.

---

## Topics

Topics are the addressing system in MQTT. They use a forward-slash hierarchy:

```
home/livingroom/temperature
home/livingroom/humidity
home/kitchen/temperature
home/kitchen/lights
```

Wildcards allow subscribing to multiple topics at once:

| Wildcard | Meaning | Example |
|---|---|---|
| `+` | Single level | `home/+/temperature` matches livingroom and kitchen |
| `#` | All remaining levels | `home/#` matches everything under home |

---

## Quality of Service (QoS)

MQTT supports three levels of message delivery guarantee:

| QoS Level | Name | Description |
|---|---|---|
| 0 | At most once | Fire and forget — message may be lost |
| 1 | At least once | Message is guaranteed to arrive but may be duplicated |
| 2 | Exactly once | Message is guaranteed to arrive exactly once |

---

## Why Use MQTT?

MQTT is ideal for:

- IoT devices and sensors
- Real-time dashboards and monitoring
- Chat and messaging applications
- Any scenario with many clients needing live updates

It is designed to be efficient with network bandwidth and works well over unreliable connections.

---

## Summary

- MQTT uses a publish/subscribe model with a central broker
- Publishers send messages to topics; subscribers receive from topics
- Topics use a `/` hierarchy with `+` and `#` wildcards
- QoS levels control message delivery guarantees
- The protocol is lightweight and well-suited for real-time web applications
