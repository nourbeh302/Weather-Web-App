<template>
  <div class="weather-card flex flex-col justify-between">
    <div class="flex-1 flex justify-between align-center">
      <button id="toggler-btn">
        <i class="ri-contrast-2-line"></i>
      </button>
      <div id="weather-city" class="flex align-center">
        <i class="ri-map-pin-2-line"></i>
        <h3>Alexandria, EG</h3>
      </div>
      <button><i class="ri-apps-2-line"></i></button>
    </div>

    <div class="flex-2 flex flex-col align-center">
      <div class="weather-icon flex justify-center align-center">
        <i class="ri-sunny-line"></i>
      </div>
      <h1 id="weather-temp">26&deg;</h1>
      <p id="weather-condition">Clear</p>
      <small id="weather-date" class="muted">Monday, 17 May</small>
    </div>

    <div class="flex-3 flex justify-between">
      <div id="wind-speed" class="flex flex-col align-center">
        <i class="ri-windy-line"></i>
        <small>4.21 km/h</small>
        <small class="muted">Wind</small>
      </div>
      <div id="humidity" class="flex flex-col align-center">
        <i class="ri-drop-line"></i>
        <small>69%</small>
        <small class="muted">Humidity</small>
      </div>
      <div id="pressure" class="flex flex-col align-center">
        <i class="ri-arrow-down-line"></i>
        <small>1024 “Hg</small>
        <small class="muted">Pressure</small>
      </div>
    </div>
  </div>
</template>