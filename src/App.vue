<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''">
    <main>
      <div class="searchbox">
        <input
          type="text"
          class="searchbar"
          placeholder="Search..."
          v-model="query"
          @keypress.enter="fetchWeather"
        />
      </div>

      <div class="weatherwrap" v-if="typeof weather.main !== 'undefined'">
        <div class="locationbox">
          <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
          <div class="date">{{ getCurrentDate() }}</div>
        </div>

        <div class="weatherbox">
          <div class="temp">{{ Math.round(weather.main.temp) }}°C</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: '', // User input for city name
      weather: {}, // Store weather data
    };
  },
  methods: {
    async fetchWeather() {
      try {
        const apiKey = '6ad69ec9f496105db87160e292b14171';
        const endpoint = 'https://api.openweathermap.org/data/2.5/weather';
        const response = await fetch(
          `${endpoint}?q=${this.query}&appid=${apiKey}&units=metric`
        );
        const data = await response.json();
        this.weather = data;
      } catch (error) {
        console.error('Error fetching weather data:', error);
      }
    },
    getCurrentDate() {
      const date = new Date();
      const options = { day: 'numeric', month: 'long', year: 'numeric' };
      return date.toLocaleDateString('en-US', options);
    },
  },
};
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  font-family: monospace;
}
#app{
  background-image: url('./assets/cold.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm{
  background-image: url('./assets/warm.jpg');
}

main{
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25),rgba(0,0,0,0.75));
}

.searchbox{
  width: 100%;
  margin-bottom: 30px;
}

.searchbox .searchbar{
  display: block;
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.5);
  transition: 0.4s;
}

.searchbox .searchbar:focus{
  box-shadow: 0px 0px 16px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.75);
  border-radius: 16px;
}

.locationbox .location{
  color: white;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,0.25);
}

.locationbox .date{
  color: white;
  font-size: 20px;
  font-weight: 300;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,0.25);
}

.weatherbox{
  text-align: center;
}

.weatherbox .temp{
  display: inline-block;
  padding: 10px 25px;
  color: white;
  font-size: 100px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.25);
  border-radius: 16px;
  margin: 30px 0px;
}

.weatherbox .weather{
  color:white;
  font-size: 40px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0,0,0,0.25);
}

</style>
