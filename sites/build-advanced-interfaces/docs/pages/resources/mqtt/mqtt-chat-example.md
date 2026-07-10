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

## Setting Up

Install the MQTT library if you have not already:

```bash
npm install mqtt
```

Create a new page at `app/chat/page.tsx` in your Next.js project. Add the `"use client"` directive since this component uses browser APIs.

---

## Component State

Start with the component structure and state variables:

```typescript
"use client";

import { useState, useEffect, useRef } from "react";
import mqtt from "mqtt";

interface ChatMessage {
    sender: string;
    text: string;
    time: string;
}

export default function ChatPage() {
    const [messages, setMessages] = useState<ChatMessage[]>([]);
    const [input, setInput] = useState("");
    const clientRef = useRef<ReturnType<typeof mqtt.connect> | null>(null);
```

- `messages` stores the array of chat messages as state
- `input` tracks the current text in the input field
- `clientRef` holds the MQTT client so it persists across re-renders

---

## Connecting and Subscribing

Use `useEffect` to connect once when the component mounts:

```typescript
    useEffect(() => {
        clientRef.current = mqtt.connect("wss://broker.hivemq.com:8884/mqtt");

        clientRef.current.on("connect", () => {
            clientRef.current?.subscribe("chat/general");
            console.log("Connected to chat");
        });

        clientRef.current.on("message", (topic: string, payload: Buffer) => {
            const data: ChatMessage = JSON.parse(payload.toString());
            setMessages((prev) => [...prev, data]);
        });

        return () => {
            clientRef.current?.end();
        };
    }, []);
```

The cleanup function in `useEffect` ends the connection when the component unmounts.

---

## Sending Messages

Publish a JSON message containing the sender, text, and timestamp:

```typescript
    function sendMessage() {
        if (input.trim() === "" || !clientRef.current) return;

        const message = {
            sender: "User",
            text: input,
            time: new Date().toLocaleTimeString()
        };

        clientRef.current.publish("chat/general", JSON.stringify(message));
        setInput("");
    }
```

The message is serialised with `JSON.stringify()` before publishing.

---

## Rendering the UI

Return the JSX for the chat interface:

```typescript
    return (
        <div>
            <h1>Chat</h1>
            <div style={{
                border: "1px solid #ccc",
                height: "300px",
                overflowY: "scroll",
                padding: "10px",
                marginBottom: "10px"
            }}>
                {messages.map((msg, i) => (
                    <div key={i}>
                        <strong>{msg.sender}</strong>
                        <span style={{ color: "gray", fontSize: "0.8em", marginLeft: "8px" }}>
                            {msg.time}
                        </span>
                        <p style={{ margin: "4px 0" }}>{msg.text}</p>
                    </div>
                ))}
            </div>
            <input
                type="text"
                value={input}
                placeholder="Type a message..."
                onChange={(e) => setInput(e.target.value)}
                onKeyDown={(e) => e.key === "Enter" && sendMessage()}
            />
            <button onClick={sendMessage}>Send</button>
        </div>
    );
}
```

The `onKeyDown` handler lets users send messages by pressing Enter.

---

## Summary

- All chat participants publish and subscribe to the same topic
- The broker handles routing each message to every subscriber automatically
- `useRef` keeps the MQTT client instance stable across React re-renders
- `useEffect` with an empty dependency array connects once on mount
- Sending JSON lets you include metadata like sender names and timestamps
- Clean up the connection in `useEffect`'s return function to prevent memory leaks
