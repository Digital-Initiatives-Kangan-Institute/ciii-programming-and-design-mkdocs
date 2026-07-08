# Real-Time Chat with MQTT

MQTT's publish/subscribe model makes it well-suited for building real-time chat applications. Multiple clients can communicate instantly through a shared topic on the broker.

---

## How It Works

Each chat participant:
1. Connects to the HiveMQ broker
2. Subscribes to a shared chat topic (e.g., `chat/general`)
3. Publishes messages to the same topic

The broker delivers each published message to every subscriber automatically.

---

## HTML Structure

A minimal chat interface needs an input field, a send button, and a display area:

```html
<div id="chat-container">
    <div id="chat-display"></div>
    <input id="message-input" type="text" placeholder="Type a message..." />
    <button id="send-btn">Send</button>
</div>

<script src="https://unpkg.com/mqtt/dist/mqtt.min.js"></script>
```

---

## Connecting and Subscribing

Connect to the broker and subscribe to the chat topic:

```javascript
const client = mqtt.connect("wss://broker.hivemq.com:8884/mqtt");

client.on("connect", function () {
    client.subscribe("chat/general");
    console.log("Connected to chat");
});
```

---

## Publishing Chat Messages

Capture user input and publish it to the topic:

```javascript
let input = document.querySelector("#message-input");
let sendBtn = document.querySelector("#send-btn");

sendBtn.addEventListener("click", function () {
    if (input.value.trim() === "") return;

    client.publish("chat/general", input.value);
    input.value = "";
});

input.addEventListener("keypress", function (event) {
    if (event.key === "Enter") {
        sendBtn.click();
    }
});
```

The `keypress` listener lets users send messages by pressing Enter.

---

## Displaying Messages

Listen for incoming messages and add them to the display:

```javascript
let display = document.querySelector("#chat-display");

client.on("message", function (topic, message) {
    let msg = document.createElement("div");
    msg.textContent = message.toString();
    msg.classList.add("chat-message");
    display.appendChild(msg);
    display.scrollTop = display.scrollHeight;
});
```

Setting `scrollTop` keeps the display scrolled to the latest message.

---

## Chat with JSON

For a richer chat experience, send JSON messages with sender names and timestamps:

```javascript
sendBtn.addEventListener("click", function () {
    let message = {
        sender: "User123",
        text: input.value,
        time: new Date().toLocaleTimeString()
    };

    client.publish("chat/general", JSON.stringify(message));
    input.value = "";
});

client.on("message", function (topic, message) {
    let data = JSON.parse(message.toString());

    let msg = document.createElement("div");
    msg.classList.add("chat-message");
    msg.innerHTML = `
        <strong>${data.sender}</strong>
        <span class="time">${data.time}</span>
        <p>${data.text}</p>
    `;
    display.appendChild(msg);
});
```

---

## Summary

- MQTT chat works by having all clients publish and subscribe to the same topic
- The broker handles routing each message to every subscriber automatically
- Adding a `keypress` listener on the input allows sending with the Enter key
- Setting `scrollTop` keeps the chat scrolled to the newest message
- Sending JSON lets you include metadata like sender names and timestamps
