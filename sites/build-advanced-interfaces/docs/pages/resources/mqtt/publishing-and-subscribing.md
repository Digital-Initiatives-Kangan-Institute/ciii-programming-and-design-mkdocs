# Publishing and Subscribing

Once connected to an MQTT broker, the two core operations are publishing messages and subscribing to topics.

---

## Publishing Messages

Use `client.publish()` to send a message to a topic:

```javascript
client.on("connect", function () {
    client.publish("myapp/sensor/value", "42.5");
});
```

The `.publish()` method takes two arguments:

1. **topic** — the destination topic string
2. **message** — the payload as a string

Messages can be published at any time after the connection is established, not only inside the `connect` callback.

---

## Specifying QoS

You can pass additional options as a third argument to control delivery guarantees:

```javascript
client.publish("myapp/sensor/value", "42.5", { qos: 1 });
```

| Option | Type | Description |
|---|---|---|
| `qos` | number | Quality of Service level (0, 1, or 2) |
| `retain` | boolean | If true, the broker keeps the last message and sends it to new subscribers |

---

## Subscribing to Topics

To receive messages, use `client.subscribe()`:

```javascript
client.on("connect", function () {
    client.subscribe("myapp/sensor/value");
});
```

You can subscribe to multiple topics at once by passing an array:

```javascript
client.subscribe(["myapp/sensor/value", "myapp/sensor/status"]);
```

---

## Handling Incoming Messages

The `message` event fires every time a message arrives on any subscribed topic:

```javascript
client.on("message", function (topic, message) {
    let value = message.toString();
    console.log("Topic:", topic);
    console.log("Message:", value);
});
```

The callback receives two arguments:

| Argument | Type | Description |
|---|---|---|
| `topic` | string | The topic the message was published to |
| `message` | Buffer | The raw message payload |

Use `.toString()` to convert the message buffer into a readable string.

---

## Subscription Order

Make sure to call `subscribe()` in the `connect` event callback. If you subscribe before the connection is established, the broker will not receive the subscription request.

---

## Summary

- `client.publish(topic, message)` sends a message to a topic
- QoS and retain options control delivery behaviour
- `client.subscribe(topic)` listens for messages on a topic
- The `message` event fires for every incoming message
- Always subscribe inside the `connect` callback
