<template>
  <div
    :class="
      typeof weather.main != 'undefined' && weather.main.temp > 25
        ? 'weather-card flex flex-col justify-between warm'
        : 'weather-card flex flex-col justify-between'
    "
  >
    <div
      class="flex-1 flex justify-between align-center"
      v-if="typeof weather.main != 'undefined'"
    >
      <button id="toggler-btn" @click="handleToggleTheme">
        <i class="ri-contrast-2-line"></i>
      </button>
      <div id="weather-city" class="flex align-center">
        <i class="ri-map-pin-2-line"></i>
        <h3>{{ weather.name }}, {{ weather.sys.country }}</h3>
      </div>
      <button><i class="ri-apps-2-line"></i></button>
    </div>

    <div
      class="flex-2 flex flex-col align-center"
      v-if="typeof weather.main != 'undefined'"
    >
      <div class="weather-icon flex justify-center align-center">
        <i
          class="ri-moon-clear-line"
          v-if="weather.weather[0].main.includes('Clear')"
        ></i>
        <i
          class="ri-cloud-line"
          v-if="weather.weather[0].main.includes('Clouds')"
        ></i>
        <i
          class="ri-rainy-line"
          v-if="weather.weather[0].main.includes('Rain')"
        ></i>
        <i
          class="ri-snowy-line"
          v-if="weather.weather[0].main.includes('Snow')"
        ></i>
        <i
          class="ri-mist-line"
          v-if="
            weather.weather[0].main.includes('Mist') ||
            weather.weather[0].main.includes('Dust') ||
            weather.weather[0].main.includes('Drizzle') ||
            weather.weather[0].main.includes('Fog')
          "
        ></i>
        <i class="ri-sunny-line" v-else></i>
      </div>
      <h1 id="weather-temp">{{ Math.round(weather.main.temp) }}&deg;</h1>
      <p id="weather-condition">{{ weather.weather[0].main }}</p>
      <small id="weather-date" class="muted">{{ getDate() }}</small>
    </div>

    <div
      class="flex-3 flex justify-between"
      v-if="typeof weather.main != 'undefined'"
    >
      <div id="wind-speed" class="flex flex-col align-center">
        <i class="ri-windy-line"></i>
        <small>{{ weather.wind.speed }} km/h</small>
        <small class="muted">Wind</small>
      </div>
      <div id="humidity" class="flex flex-col align-center">
        <i class="ri-drop-line"></i>
        <small>{{ weather.main.humidity }}%</small>
        <small class="muted">Humidity</small>
      </div>
      <div id="pressure" class="flex flex-col align-center">
        <i class="ri-arrow-down-line"></i>
        <small>{{ weather.main.pressure }} “Hg</small>
        <small class="muted">Pressure</small>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment';
export default {
  name: "WeatherCard",
  props: ["weather"],
  methods: {
    getDate() {
      return moment().format("dddd, DD MMM");
    },
    handleToggleTheme() {
      this.$emit("toggle-theme")
    },
  },
};
</script>