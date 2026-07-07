# Weather Widget

Practice async JavaScript and fetch by building a weather widget that displays current conditions for a city.

---

## Setup

!!! abstract "Instructions"
    Create `weather.html`, `weather.css`, and `weather.js`. We will use a free weather API:

    ```
    https://api.open-meteo.com/v1/forecast
    ```

    This API does not require an API key and expects `latitude` and `longitude` parameters.

---

## Task 1: Understand the API

!!! abstract "Instructions"
    Before writing code, explore the API in your browser:

    ```
    https://api.open-meteo.com/v1/forecast?latitude=-37.814&longitude=144.9633&current_weather=true
    ```

    This returns current weather for Melbourne. Try changing the coordinates to your city.

    The response looks like:

    ```json
    {
        "current_weather": {
            "temperature": 22.5,
            "windspeed": 15.2,
            "winddirection": 180,
            "weathercode": 1
        }
    }
    ```

---

## Task 2: Build the HTML Structure

!!! abstract "Instructions"
    Create a simple layout with:

    - A heading
    - A city name input and a search button
    - A weather display area (initially empty or showing "Search for a city")
    - A loading message (hidden by default)
    - An error message area (hidden by default)

??? code "HTML"
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Weather Widget</title>
        <link rel="stylesheet" href="weather.css">
    </head>
    <body>
        <div class="widget">
            <h1>Weather</h1>

            <div class="search">
                <input type="text" id="cityInput" placeholder="Enter city name...">
                <button id="searchBtn">Search</button>
            </div>

            <p id="loading" class="hidden">Loading...</p>
            <p id="error" class="hidden"></p>

            <div id="weatherDisplay" class="hidden">
                <h2 id="cityName"></h2>
                <p id="temperature"></p>
                <p id="wind"></p>
                <p id="description"></p>
            </div>
        </div>

        <script src="weather.js"></script>
    </body>
    </html>
    ```

---

## Task 3: Select Elements

!!! abstract "Instructions"
    In `weather.js`, select all DOM elements and store them in variables.

    Define a `coordinates` object mapping city names to latitude/longitude:

    ```javascript
    const cities = {
        "melbourne": { lat: -37.814, lon: 144.9633 },
        "sydney": { lat: -33.8688, lon: 151.2093 },
        "brisbane": { lat: -27.4698, lon: 153.0251 },
        "perth": { lat: -31.9505, lon: 115.8605 },
        "adelaide": { lat: -34.9285, lon: 138.6007 },
        "hobart": { lat: -42.8821, lon: 147.3272 },
        "darwin": { lat: -12.4628, lon: 130.8417 },
        "canberra": { lat: -35.2809, lon: 149.1300 }
    };
    ```

---

## Task 4: Fetch Weather Data

!!! abstract "Instructions"
    Create an `async` function called `getWeather(city)` that:

    1. Looks up the city in the `cities` object
    2. If the city is not found, throws an error: "City not found"
    3. If found, fetches data from the Open-Meteo API using coordinates
    4. Returns the `current_weather` object

    Use `async/await` and `try/catch`.

??? code "Starter"
    ```javascript
    async function getWeather(city) {
        const coords = cities[city.toLowerCase()];
        if (!coords) {
            throw new Error(`City "${city}" not found.`);
        }

        const url = `https://api.open-meteo.com/v1/forecast?latitude=${coords.lat}&longitude=${coords.lon}&current_weather=true`;

        const response = await fetch(url);
        if (!response.ok) {
            throw new Error(`API error: ${response.status}`);
        }

        const data = await response.json();
        return data.current_weather;
    }
    ```

??? hint "Hint - Testing"
    Test your function in the console:
    ```javascript
    getWeather("melbourne").then(data => console.log(data));
    getWeather("paris").catch(err => console.error(err));
    ```

---

## Task 5: Display Weather Data

!!! abstract "Instructions"
    Create a function `displayWeather(city, weather)` that:

    1. Shows the weather display area (remove `hidden` class)
    2. Shows the city name (capitalise the first letter)
    3. Shows the temperature with the unit (°C)
    4. Shows the wind speed with the unit (km/h)
    5. Shows a weather description based on the `weathercode`

    Weather codes:
    - 0: Clear sky
    - 1, 2, 3: Partly cloudy
    - 45, 48: Fog
    - 51, 53, 55: Drizzle
    - 61, 63, 65: Rain
    - 71, 73, 75: Snow
    - 80, 81, 82: Rain showers
    - 95, 96, 99: Thunderstorm

??? hint "Hint - Click to expand"
    ```javascript
    function getWeatherDescription(code) {
        if (code === 0) return "Clear sky";
        if (code >= 1 && code <= 3) return "Partly cloudy";
        if (code === 45 || code === 48) return "Fog";
        if (code >= 51 && code <= 55) return "Drizzle";
        if (code >= 61 && code <= 65) return "Rain";
        if (code >= 71 && code <= 75) return "Snow";
        if (code >= 80 && code <= 82) return "Rain showers";
        if (code >= 95 && code <= 99) return "Thunderstorm";
        return "Unknown";
    }

    function displayWeather(city, weather) {
        document.getElementById("cityName").textContent =
            city.charAt(0).toUpperCase() + city.slice(1);
        document.getElementById("temperature").textContent =
            `Temperature: ${weather.temperature}°C`;
        document.getElementById("wind").textContent =
            `Wind: ${weather.windspeed} km/h`;
        document.getElementById("description").textContent =
            getWeatherDescription(weather.weathercode);
        document.getElementById("weatherDisplay").classList.remove("hidden");
    }
    ```

---

## Task 6: Connect the Search Button

!!! abstract "Instructions"
    When the user clicks "Search":

    1. Get the city from the input
    2. If the input is empty, show an error
    3. Show the loading message and hide previous results/errors
    4. Call `getWeather()` and then `displayWeather()`
    5. Handle errors by showing them in the error area
    6. Hide the loading message when done (in `finally`)

??? hint "Hint - Click to expand"
    ```javascript
    document.getElementById("searchBtn").addEventListener("click", async function() {
        const city = document.getElementById("cityInput").value.trim();
        const loading = document.getElementById("loading");
        const error = document.getElementById("error");
        const display = document.getElementById("weatherDisplay");

        if (!city) {
            error.textContent = "Please enter a city name.";
            error.classList.remove("hidden");
            return;
        }

        // Reset state
        error.classList.add("hidden");
        display.classList.add("hidden");
        loading.classList.remove("hidden");

        try {
            const weather = await getWeather(city);
            displayWeather(city, weather);
        } catch (err) {
            error.textContent = err.message;
            error.classList.remove("hidden");
        } finally {
            loading.classList.add("hidden");
        }
    });
    ```

---

## Task 7: Search on Enter Key

!!! abstract "Instructions"
    Allow the user to press the Enter key in the city input to trigger the search (without clicking the button).

??? hint "Hint - Click to expand"
    ```javascript
    document.getElementById("cityInput").addEventListener("keydown", function(event) {
        if (event.key === "Enter") {
            document.getElementById("searchBtn").click();
        }
    });
    ```

---

## Task 8: Style the Widget

!!! abstract "Instructions"
    Style the weather widget to look like a real weather app card. Use flexbox for centring and layout.

??? hint "Hint - CSS"
    ```css
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        margin: 0;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        font-family: Arial, sans-serif;
    }

    .widget {
        background: white;
        padding: 2rem;
        border-radius: 12px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        width: 350px;
        text-align: center;
    }

    .search {
        display: flex;
        gap: 0.5rem;
        margin-bottom: 1.5rem;
    }

    .search input {
        flex: 1;
        padding: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 4px;
    }

    button {
        padding: 0.5rem 1rem;
        background-color: #667eea;
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
    }

    button:hover {
        background-color: #5a6fd6;
    }

    #weatherDisplay {
        background: #f8f9fa;
        padding: 1rem;
        border-radius: 8px;
    }

    #temperature {
        font-size: 2.5rem;
        font-weight: bold;
        margin: 0.5rem 0;
    }

    .hidden {
        display: none;
    }

    #error {
        color: #e53935;
    }

    #loading {
        color: #666;
    }
    ```

---

## Requirements

- Use `async/await` (not `.then()` chains)
- Use `try/catch/finally` for error handling
- Check `response.ok` before parsing JSON
- Show a loading state while the fetch is in progress
- Handle errors (invalid city, network failure) with user-friendly messages
- Support at least 5 cities in the coordinates object
- The Enter key triggers the search
