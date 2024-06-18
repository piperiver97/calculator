<script>
import clearImage from '@/assets/sol.jpg';
import cloudyImage from '@/assets/nubes.jpg';
import rainImage from '@/assets/lluvia.jpg';
import stormyImage from '@/assets/storm.jpg';
import defaultImage from '@/assets/default.jpg';

export default {
  data() {
    return {
      cities: [],
      selectedCity: null,
      weather: null,
      loading: false,
      error: null,
    };
  },
  methods: {
    async fetchWeatherData() {
      this.loading = true;
      this.error = null;
      try {
        const response = await fetch('https://www.el-tiempo.net/api/json/v2/provincias/33'); // Provincia de Asturias
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        this.cities = data.ciudades;
        this.updateWeather(); 
      } catch (error) {
        this.error = 'There was a problem fetching the weather data.';
      } finally {
        this.loading = false;
      }
    },
    updateWeather() {
      if (this.selectedCity) {
        const cityWeather = this.selectedCity;
        this.weather = {
          city: this.decode(cityWeather.name),
          stateSky: cityWeather.stateSky.description,
          temperatureMin: cityWeather.temperatures.min,
          temperatureMax: cityWeather.temperatures.max
        };
      }
    },
    getImage(description) {
      switch (description) {
        case 'Despejado':
          return clearImage;
        case 'Nuboso con lluvia':
        case 'Muy nuboso con lluvia':
        case 'Cubierto con lluvia':
        case 'Intervalos nubosos con lluvia':
          return rainImage;
        case 'Nuboso':
        case 'Muy nuboso':
          return cloudyImage;
        case 'Nuboso con tormenta':
        return stormyImage;
        default:
          return defaultImage;
      }
    },
    decode(text) {
      try {
        return decodeURIComponent(escape(text));
      } catch (e) {
        return text;
      }
    }
  }
};
</script>

<template>
  <div class="container">
    <!-- <h1>Weather</h1> -->
    <button @click="fetchWeatherData" class="btn">Check the weather!</button>
    <div v-if="loading">Loading...</div>
    <div v-if="error" class="alert alert-danger">{{ error }}</div>
    <div v-if="cities && cities.length > 0">
      <label for="city-select">Select a city:</label>
      <select id="city-select" v-model="selectedCity" @change="updateWeather">
        <option v-for="city in cities" :key="city.id" :value="city">{{ decode(city.name) }}</option>
      </select>
    </div>
    <div v-if="weather" class="weather-card card">
      <img :src="getImage(weather.stateSky)" class="card-img-top" :alt="weather.stateSky" />
      <div class="card-body">
        <h5 class="card-title">{{ weather.city }}</h5>
        <p class="card-text">{{ weather.stateSky }}</p>
        <p class="card-text">Temperatura: Min {{ weather.temperatureMin }}°C, Max {{ weather.temperatureMax }}°C</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  padding-top: 20px;
  text-align: center;
}

.weather-card {
  max-width: 400px;
  margin: 20px auto;
}

.card-img-top {
  height: auto;
  max-width: 100%;
}

.card-body {
  text-align: left;
}

label {
  margin-top: 20px;
}

select {
  display: block;
  margin: 10px auto;
}

.btn{
  background-color: #4bade2;
  color: white;
}

.btn:hover {
  color: #fff;
  background-color: #93ddff;
  border-color: #93ddff;
}

.weather-card {
  background-color: rgb(66, 66, 66);
  color: white;
}

</style>

