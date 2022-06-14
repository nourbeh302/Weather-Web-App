<template>
  <div id="app" ref="app">
    <WeatherCard :weather="weather" @toggle-theme="toggleTheme" />
    <div class="input-wrapper">
      <h2>Search</h2>
      <div class="flex align-center">
        <i class="ri-search-line"></i>
        <input type="text" placeholder="Enter a city name" v-model="query" @keypress.enter="fetchWeather" />
      </div>
    </div>
  </div>
</template>

<script>
import "./css/App.css";
import "./css/Flex.css";
import WeatherCard from "./components/WeatherCard.vue";

export default {
  name: "App",
  components: {WeatherCard},
  data() {
    return {
      url_base: "https://api.openweathermap.org/data/2.5/",
      API_KEY: "f7c027b1b241ccf6d88a052db4a59c58",
      query: "",
      weather: {}
    };
  },
  methods: {
    fetchWeather() {
      if (this.query == "") this.query = "Cairo";
      fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.API_KEY}`)
        .then((res) => res.json())
        .then((data) => (this.weather = data));
    },
    toggleTheme() {
      this.$refs["app"].toggleAttribute("light-mode");
    },
  },
};
</script>
