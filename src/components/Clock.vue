<script setup lang="ts">
import { onMounted, ref } from 'vue'

const hours = ref(0)
const minutes = ref(0)
const seconds = ref(0)

const sleep = (ms: number) => new Promise(resolve => setTimeout(resolve, ms))

const updateClockHands = async () => {
  const date = new Date()
  hours.value = date.getHours()
  minutes.value = date.getMinutes()
  seconds.value = date.getSeconds()
  const hourHandContainer: HTMLElement = document.querySelector('.hour-hand-container')!
  const minuteHandContainer: HTMLElement = document.querySelector('.minute-hand-container')!
  const secondHandContainer: HTMLElement = document.querySelector('.second-hand-container')!

  if (hours.value === 0) {
    hourHandContainer.style.setProperty('--i', '60')
    await sleep(600)
    hourHandContainer.style.setProperty('--t', '0s')
    hourHandContainer.style.setProperty('--i', '0')
    await sleep(1)
    hourHandContainer.style.setProperty('--t', '0.5s')
  } else {
    hourHandContainer.style.setProperty('--i', `${hours.value + minutes.value / 60}`)
  }

  if (minutes.value === 0) {
    minuteHandContainer.style.setProperty('--i', '60')
    await sleep(600)
    minuteHandContainer.style.setProperty('--t', '0s')
    minuteHandContainer.style.setProperty('--i', '0')
    await sleep(1)
    minuteHandContainer.style.setProperty('--t', '0.5s')
  } else {
    minuteHandContainer.style.setProperty('--i', `${minutes.value + seconds.value / 60}`)
  }

  if (seconds.value === 0) {
    secondHandContainer.style.setProperty('--i', '60')
    await sleep(600)
    secondHandContainer.style.setProperty('--t', '0s')
    secondHandContainer.style.setProperty('--i', '0')
    await sleep(1)
    secondHandContainer.style.setProperty('--t', '0.5s')
  } else {
    secondHandContainer.style.setProperty('--i', `${seconds.value}`)
  }
}

onMounted(async () => {
  const hourHandContainer: HTMLElement = document.querySelector('.hour-hand-container')!
  const minuteHandContainer: HTMLElement = document.querySelector('.minute-hand-container')!
  const secondHandContainer: HTMLElement = document.querySelector('.second-hand-container')!
  hourHandContainer.style.setProperty('--t', '0.5s')
  minuteHandContainer.style.setProperty('--t', '0.5s')
  secondHandContainer.style.setProperty('--t', '0.5s')

  while (true) {
    updateClockHands()
    await sleep(1000)
  }
})
</script>

<template>
  <div class="clock">
    <div class="clock-hour-mark-container" style="--i: 0;">
      <div class="clock-hour-mark">12</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 1;">
      <div class="clock-hour-mark">1</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 2;">
      <div class="clock-hour-mark">2</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 3;">
      <div class="clock-hour-mark">3</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 4;">
      <div class="clock-hour-mark">4</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 5;">
      <div class="clock-hour-mark">5</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 6;">
      <div class="clock-hour-mark">6</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 7;">
      <div class="clock-hour-mark">7</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 8;">
      <div class="clock-hour-mark">8</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 9;">
      <div class="clock-hour-mark">9</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 10;">
      <div class="clock-hour-mark">10</div>
    </div>
    <div class="clock-hour-mark-container" style="--i: 11;">
      <div class="clock-hour-mark">11</div>
    </div>
    <div class="second-hand-container">
      <div class="second-hand"></div>
    </div>
    <div class="clock-center-second"></div>
    <div class="clock-center"></div>
    <div class="hour-hand-container">
      <div class="hour-hand"></div>
    </div>
    <div class="clock-center-hour"></div>
    <div class="minute-hand-container">
      <div class="minute-hand"></div>
    </div>
    <div class="clock-center-minute"></div>
    <div :class="{ now: seconds === 0 }" class="clock-scale-container" style="--i: 0;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 1 }" class="clock-scale-container" style="--i: 1;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 2 }" class="clock-scale-container" style="--i: 2;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 3 }" class="clock-scale-container" style="--i: 3;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 4 }" class="clock-scale-container" style="--i: 4;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 5 }" class="clock-scale-container" style="--i: 5;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 6 }" class="clock-scale-container" style="--i: 6;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 7 }" class="clock-scale-container" style="--i: 7;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 8 }" class="clock-scale-container" style="--i: 8;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 9 }" class="clock-scale-container" style="--i: 9;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 10 }" class="clock-scale-container" style="--i: 10;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 11 }" class="clock-scale-container" style="--i: 11;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 12 }" class="clock-scale-container" style="--i: 12;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 13 }" class="clock-scale-container" style="--i: 13;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 14 }" class="clock-scale-container" style="--i: 14;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 15 }" class="clock-scale-container" style="--i: 15;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 16 }" class="clock-scale-container" style="--i: 16;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 17 }" class="clock-scale-container" style="--i: 17;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 18 }" class="clock-scale-container" style="--i: 18;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 19 }" class="clock-scale-container" style="--i: 19;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 20 }" class="clock-scale-container" style="--i: 20;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 21 }" class="clock-scale-container" style="--i: 21;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 22 }" class="clock-scale-container" style="--i: 22;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 23 }" class="clock-scale-container" style="--i: 23;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 24 }" class="clock-scale-container" style="--i: 24;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 25 }" class="clock-scale-container" style="--i: 25;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 26 }" class="clock-scale-container" style="--i: 26;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 27 }" class="clock-scale-container" style="--i: 27;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 28 }" class="clock-scale-container" style="--i: 28;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 29 }" class="clock-scale-container" style="--i: 29;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 30 }" class="clock-scale-container" style="--i: 30;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 31 }" class="clock-scale-container" style="--i: 31;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 32 }" class="clock-scale-container" style="--i: 32;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 33 }" class="clock-scale-container" style="--i: 33;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 34 }" class="clock-scale-container" style="--i: 34;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 35 }" class="clock-scale-container" style="--i: 35;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 36 }" class="clock-scale-container" style="--i: 36;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 37 }" class="clock-scale-container" style="--i: 37;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 38 }" class="clock-scale-container" style="--i: 38;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 39 }" class="clock-scale-container" style="--i: 39;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 40 }" class="clock-scale-container" style="--i: 40;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 41 }" class="clock-scale-container" style="--i: 41;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 42 }" class="clock-scale-container" style="--i: 42;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 43 }" class="clock-scale-container" style="--i: 43;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 44 }" class="clock-scale-container" style="--i: 44;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 45 }" class="clock-scale-container" style="--i: 45;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 46 }" class="clock-scale-container" style="--i: 46;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 47 }" class="clock-scale-container" style="--i: 47;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 48 }" class="clock-scale-container" style="--i: 48;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 49 }" class="clock-scale-container" style="--i: 49;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 50 }" class="clock-scale-container" style="--i: 50;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 51 }" class="clock-scale-container" style="--i: 51;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 52 }" class="clock-scale-container" style="--i: 52;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 53 }" class="clock-scale-container" style="--i: 53;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 54 }" class="clock-scale-container" style="--i: 54;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 55 }" class="clock-scale-container" style="--i: 55;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 56 }" class="clock-scale-container" style="--i: 56;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 57 }" class="clock-scale-container" style="--i: 57;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 58 }" class="clock-scale-container" style="--i: 58;">
      <div class="clock-scale"></div>
    </div>
    <div :class="{ now: seconds === 59 }" class="clock-scale-container" style="--i: 59;">
      <div class="clock-scale"></div>
    </div>
  </div>
</template>

<style scoped>
.clock {
  aspect-ratio: var(--ratio-square);
  display: grid;
  place-items: center;
  position: relative;
  width: 75vmin;

  background-color: var(--grape-0);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
}

.hour-hand-container {
  height: calc(75% - 1rem);
  padding-top: 1rem;
  position: absolute;
  width: 1rem;

  transform: rotate(calc(1deg * 30 * var(--i)));
  transition-duration: var(--t);
}

.minute-hand-container {
  height: calc(85% - 1rem);
  padding-top: 1rem;
  position: absolute;
  width: 0.5rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
  transition-duration: var(--t);
}

.second-hand-container {
  height: calc(95% - 1rem);
  padding-top: 1rem;
  position: absolute;
  width: 0.5rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
  transition-duration: var(--t);
}

.hour-hand {
  height: 50%;
  width: inherit;

  background-color: var(--green-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-3);
  opacity: 0.75;
}

.minute-hand {
  height: 50%;
  width: inherit;

  background-color: var(--yellow-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-4);
  opacity: 0.75;
}

.second-hand {
  height: 70%;
  width: inherit;

  background-color: var(--red-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
  opacity: 0.75;
}

.clock-center-hour {
  aspect-ratio: var(--ratio-square);
  position: absolute;
  width: 1.5rem;

  background-color: var(--green-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-3);
}

.clock-center-minute {
  aspect-ratio: var(--ratio-square);
  position: absolute;
  width: 1rem;

  background-color: var(--yellow-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-4);
}

.clock-center-second {
  aspect-ratio: var(--ratio-square);
  position: absolute;
  width: 2.5rem;

  background-color: var(--red-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
}

.clock-center {
  aspect-ratio: var(--ratio-square);
  position: absolute;
  width: 2rem;

  background-color: var(--blue-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-2);
}

.clock-scale-container {
  height: 100%;
  padding-top: 0.5rem;
  position: absolute;
  width: 0.2rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
  transition-duration: 0.1s;
}

.clock-scale-container:nth-child(5n) {
  height: 100%;
  padding-top: 0.5rem;
  position: absolute;
  width: 0.4rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
  transition-duration: 0.1s;
}

.clock-scale-container.now {
  width: 0.3rem;
}

.clock-scale-container.now:nth-child(5n) {
  width: 0.5rem;
}

.clock-scale-container:nth-child(5n) .clock-scale {
  background-color: var(--grape-2);
}

.clock-scale-container.now:nth-child(5n) .clock-scale {
  background-color: var(--red-6);
}

.clock-scale {
  aspect-ratio: var(--ratio-square);
  position: absolute;
  width: inherit;

  background-color: var(--grape-1);
  border-radius: var(--radius-round);
  box-shadow: var(--inner-shadow-1);
}

.now .clock-scale {
  background-color: var(--red-5);
}

.clock-hour-mark-container {
  height: 100%;
  padding-top: 1.5rem;
  position: absolute;

  transform: rotate(calc(1deg * 30 * var(--i)));
}

.clock-hour-mark {
  color: var(--gray-9);
  font-family: 'Poppins', var(--font-sans);
  font-size: 1rem;
  font-weight: var(--font-weight-7);
  text-shadow: var(--shadow-1);
  transform: rotate(calc(1deg * -30 * var(--i)));
}

@media (prefers-color-scheme: dark) {
  .clock {
    background-color: var(--gray-9);
  }

  .hour-hand {
    background-color: var(--green-9);
  }

  .minute-hand {
    background-color: var(--yellow-9);
  }

  .second-hand {
    background-color: var(--red-9);
  }

  .clock-center-hour {
    background-color: var(--green-9);
  }

  .clock-center-minute {
    background-color: var(--yellow-9);
  }

  .clock-center-second {
    background-color: var(--red-9);
  }

  .clock-center {
    background-color: var(--blue-9);
  }

  .clock-scale-container:nth-child(5n) .clock-scale {
    background-color: var(--gray-7);
  }

  .clock-scale-container.now:nth-child(5n) .clock-scale {
    background-color: var(--red-8);
  }

  .clock-scale {
    background-color: var(--gray-8);
  }

  .now .clock-scale {
    background-color: var(--red-9);
  }

  .clock-hour-mark {
    color: var(--gray-0);
  }
}
</style>

