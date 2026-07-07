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
        // 1. Look up the city in the cities object (use toLowerCase())
        const coords = cities[city.toLowerCase()];

        // 2. If coords is undefined, throw an Error with a message

        // 3. Build the URL string using coords.lat and coords.lon

        // 4. Use await fetch() to get the response

        // 5. Check response.ok — throw an Error if not ok

        // 6. Parse the JSON with await response.json()

        // 7. Return data.current_weather
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
    3. Shows the temperature with the unit (C)
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
    - Create a helper function `getWeatherDescription(code)` that returns a human-readable string for each weather code range. Look at the weather code table above and use `if` statements to check the ranges.
    - Create a `displayWeather(city, weather)` function that:
      - Capitalises the city name (use `charAt(0).toUpperCase()` with `slice(1)` for the rest).
      - Updates the `textContent` of the temperature, wind, and description elements with the data from the `weather` object (the API returns `temperature`, `windspeed`, and `weathercode`).
      - Removes the `"hidden"` class from the weather display area to make it visible.

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
    - Add a `click` event listener to the search button. Use `async` on the callback function so you can `await` inside it.
    - Get the trimmed city value from the input. If empty, show the error element (remove its `"hidden"` class) with an appropriate message, then `return`.
    - Before fetching: hide the error and weather display, show the loading element.
    - Use a `try` block to `await getWeather(city)` and pass the result to `displayWeather()`.
    - Use a `catch` block to show the error message (from `err.message`) in the error element.
    - Use a `finally` block to hide the loading element (it runs whether the request succeeded or failed).

---

## Task 7: Search on Enter Key

!!! abstract "Instructions"
    Allow the user to press the Enter key in the city input to trigger the search (without clicking the button).

??? hint "Hint - Click to expand"
    - Add a `keydown` event listener to the city input element.
    - Check if `event.key` is `"Enter"`.
    - If it is, you can trigger the search by calling `.click()` on the search button element.

---

## Task 8: Style the Widget

!!! abstract "Instructions"
    Style the weather widget to look like a real weather app card. Use flexbox for centring and layout.

??? hint "Hint - CSS"
    - **Body:** Use `display: flex`, `justify-content: center`, `align-items: center`, and `min-height: 100vh` to centre the widget vertically and horizontally. Add a gradient `background` for visual appeal.
    - **Widget card:** Give it a white `background`, `padding`, `border-radius`, and `box-shadow` for depth. Set a fixed `width` around 350px.
    - **Search area:** Use `display: flex` with `gap` to put the input and button side by side. Let the input grow with `flex: 1`.
    - **Button:** Match the gradient colours — use a purple/blue `background-color`, white text, no border, rounded corners, and `cursor: pointer`. Darken on `:hover`.
    - **Weather display:** Give it a light background and padding. Make the temperature large with `font-size`.
    - **Hidden/Error/Loading:** Use a `.hidden` class with `display: none`. Style `#error` in red and `#loading` in grey.

---

## Requirements

- Use `async/await` (not `.then()` chains)
- Use `try/catch/finally` for error handling
- Check `response.ok` before parsing JSON
- Show a loading state while the fetch is in progress
- Handle errors (invalid city, network failure) with user-friendly messages
- Support at least 5 cities in the coordinates object
- The Enter key triggers the search
