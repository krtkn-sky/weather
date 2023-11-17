# Vue Weather App

![image](https://github.com/krtkn-sky/weather/assets/121655285/3a11aab5-da28-4d9c-b59f-8ad618d86ed9)

![image](https://github.com/krtkn-sky/weather/assets/121655285/0b0be612-906b-40c2-94ee-329e3f757db2)

A simple Vue.js application that allows users to search for the current weather in a city using the OpenWeather API.

## Features

- Dynamic background based on temperature (cold or warm).
- Real-time weather information display.
- Responsive design for an enhanced user experience.

## Getting Started

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your-username/vue-weather-app.git
   ```

2. Navigate to the project directory:

   ```bash
   cd vue-weather-app
   ```

3. Install dependencies:

   ```bash
   npm install
   ```

4. Add your OpenWeather API key in the `fetchWeather` method in `src/App.vue`:

   ```javascript
   const apiKey = 'YOUR_OPENWEATHER_API_KEY';
   ```

5. Run the application:

   ```bash
   npm run serve
   ```

6. Open your browser and visit [http://localhost:8080/](http://localhost:8080/) to view the app.

## Screenshots


## Technologies Used

- Vue.js
- OpenWeather API

## Styling

The application uses a combination of CSS and dynamic background images to create an immersive user interface. The styling is responsive and adjusts based on the temperature to provide a visual representation of the weather.

### CSS Classes

- `#app`: Main container with a dynamic background based on temperature.
- `.searchbox`: Container for the search bar.
- `.searchbox .searchbar`: Styling for the search input.
- `.locationbox .location`: Styling for the location information.
- `.locationbox .date`: Styling for the date information.
- `.weatherbox`: Container for weather information.
- `.weatherbox .temp`: Styling for the temperature display.
- `.weatherbox .weather`: Styling for the weather description.
