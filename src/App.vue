<template>
  <div id="app">
    <WeatherCard />
    <div class="input-wrapper">
      <h2>Search</h2>
      <div class="flex align-center">
        <i class="ri-search-line"></i>
        <input type="text" placeholder="Enter a city name" />
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
  components: { WeatherCard },
};
</script>
