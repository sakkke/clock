<script setup lang="ts">
import { onMounted } from 'vue'

const updateClockHands = () => {
  const date = new Date()
  const hours = date.getHours()
  const minutes = date.getMinutes()
  const seconds = date.getSeconds()
  ; (document.querySelector('.hour-hand-container') as HTMLElement)
    .style.setProperty('--i', hours.toString())
  ; (document.querySelector('.minute-hand-container') as HTMLElement)
    .style.setProperty('--i', minutes.toString())
  ; (document.querySelector('.second-hand-container') as HTMLElement)
    .style.setProperty('--i', seconds.toString())
}

onMounted(() => {
  updateClockHands()
  setInterval(() => {
    updateClockHands()
  }, 1000)
})
</script>

<template>
  <div class="clock">
    <div class="hour-hand-container">
      <div class="hour-hand"></div>
    </div>
    <div class="minute-hand-container">
      <div class="minute-hand"></div>
    </div>
    <div class="second-hand-container">
      <div class="second-hand"></div>
    </div>
    <div class="clock-center"></div>
  </div>
</template>

<style scoped>
.clock {
  aspect-ratio: var(--ratio-square);
  display: grid;
  place-items: center;
  position: relative;
  width: 256px;

  background-color: var(--grape-0);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
}

.hour-hand-container {
  height: 75%;
  position: absolute;
  width: 1.5rem;

  transform: rotate(calc(1deg * 30 * var(--i)));
}

.minute-hand-container {
  height: 85%;
  position: absolute;
  width: 1rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
}

.second-hand-container {
  height: 95%;
  position: absolute;
  width: .5rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
}

.hour-hand {
  height: 50%;
  width: inherit;

  background-color: var(--green-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
}

.minute-hand {
  height: 50%;
  width: inherit;

  background-color: var(--yellow-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
}

.second-hand {
  height: 50%;
  width: inherit;

  background-color: var(--red-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
}

.clock-center {
  height: 2rem;
  position: absolute;
  width: 2rem;

  background-color: var(--blue-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-2);
}
</style>

