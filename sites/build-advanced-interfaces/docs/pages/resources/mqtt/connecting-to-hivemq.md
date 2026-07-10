# Connecting to HiveMQ

[HiveMQ](https://www.hivemq.com) provides a free public MQTT broker and a browser-compatible JavaScript client library. This makes it ideal for adding real-time messaging to web applications.

---

## The Public Broker

The HiveMQ public broker is available at:

```
wss://broker.hivemq.com:8884/mqtt
```

> **wss://** stands for WebSocket Secure — it allows browser JavaScript to connect to the broker over HTTPS without any special configuration.

The public broker is free for anyone to use but has no authentication or access control. Anyone can publish or subscribe to any topic, so use unique topic names to avoid collisions.

---

## Installing the MQTT Library

Install the `mqtt` package via npm from inside your Next.js project:

```bash
npm install mqtt
```

This adds the MQTT client library to your project's `package.json` and `node_modules`.

The library exposes the same API as the CDN version but uses ES modules. Import it at the top of any file that needs it:

```typescript
import mqtt from "mqtt";
```

The `"use client"` directive is required when using MQTT in Next.js, since the browser WebSocket connection is a client-side operation.

---

## Connecting to the Broker

Use `mqtt.connect()` to establish a connection:

```typescript
import mqtt from "mqtt";

const client = mqtt.connect("wss://broker.hivemq.com:8884/mqtt");

client.on("connect", () => {
    console.log("Connected to MQTT broker");
});
```

The `connect` event fires when the connection is successfully established. Only after this event should you publish or subscribe.

---

## Handling Connection Errors

Always handle the case where the connection fails:

```typescript
client.on("error", (error: Error) => {
    console.error("Connection failed:", error);
});
```

This ensures your application degrades gracefully if the broker is unreachable.

---

## Client IDs

Each client connecting to an MQTT broker should have a unique ID. If you do not specify one, a random ID is generated:

```typescript
const client = mqtt.connect("wss://broker.hivemq.com:8884/mqtt", {
    clientId: "my-app-" + Math.random().toString(16).slice(2)
});
```

On the public broker, using a unique client ID prevents session conflicts with other users.

---

## The Connection Object

The `client` object returned by `mqtt.connect()` is your interface to the broker. All MQTT operations — publishing, subscribing, and handling messages — are done through this object.

---

## Summary

- HiveMQ provides a free public MQTT broker at `wss://broker.hivemq.com:8884/mqtt`
- Install the library with `npm install mqtt` and import it with `import mqtt from "mqtt"`
- `mqtt.connect(url)` creates a connection and returns a client object
- Wait for the `connect` event before performing MQTT operations
- Handle the `error` event to manage connection failures
- Use a unique `clientId` to avoid conflicts on the public broker
