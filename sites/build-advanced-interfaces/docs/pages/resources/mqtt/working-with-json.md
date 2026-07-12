# Working with JSON

MQTT messages are plain strings, but you can send structured data by encoding objects as JSON.

---

## Why JSON?

Most real-world data is structured — a sensor reading might include a temperature value, a unit, and a timestamp. JSON lets you send this as a single message rather than multiple separate publishes.

---

## Publishing JSON

Use `JSON.stringify()` to convert a JavaScript object to a string before publishing:

```javascript
let data = {
    sensor: "motion",
    value: true,
    timestamp: Date.now()
};

client.publish("myapp/sensor/motion", JSON.stringify(data));
```

The object is serialised into a string like:

```json
{"sensor":"motion","value":true,"timestamp":1752004800000}
```

---

## Receiving JSON

Use `JSON.parse()` to convert the incoming message string back into a JavaScript object:

```javascript
client.on("message", function (topic, message) {
    let data = JSON.parse(message.toString());

    console.log("Sensor:", data.sensor);
    console.log("Value:", data.value);
    console.log("Time:", new Date(data.timestamp).toLocaleTimeString());
});
```

---

## Sending Arrays

JSON supports arrays, so you can send collections of items:

```javascript
let readings = [
    { sensor: "temp", value: 22.5 },
    { sensor: "humidity", value: 60 },
    { sensor: "pressure", value: 1013 }
];

client.publish("myapp/sensor/all", JSON.stringify(readings));
```

---

## Error Handling

JSON parsing can fail if the message is not valid JSON. Wrap it in a try/catch block:

```javascript
client.on("message", function (topic, message) {
    try {
        let data = JSON.parse(message.toString());
        console.log("Parsed:", data);
    } catch (error) {
        console.error("Invalid JSON received:", message.toString());
    }
});
```

---

## Displaying JSON Data in the DOM

Once parsed, you can display the data on the page:

```javascript
client.on("message", function (topic, message) {
    let data = JSON.parse(message.toString());

    let card = document.createElement("div");
    card.innerHTML = `
        <h3>${data.sensor}</h3>
        <p>Value: ${data.value}</p>
        <p>Updated: ${new Date(data.timestamp).toLocaleTimeString()}</p>
    `;

    document.querySelector("#dashboard").prepend(card);
});
```

---

## Summary

- Use `JSON.stringify()` to encode objects as strings before publishing
- Use `JSON.parse()` to decode received message strings back into objects
- Arrays and nested objects are fully supported
- Wrap JSON parsing in try/catch to handle invalid messages gracefully
- Parsed JSON data can be displayed in the DOM like any other JavaScript data
