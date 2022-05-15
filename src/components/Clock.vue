<script setup lang="ts">
import { onMounted } from 'vue'

const sleep = (ms: number) => new Promise(resolve => setTimeout(resolve, ms))

const updateClockHands = async () => {
  const date = new Date()
  const hours = date.getHours()
  const minutes = date.getMinutes()
  const seconds = date.getSeconds()
  const hourHandContainer: HTMLElement = document.querySelector('.hour-hand-container')!
  const minuteHandContainer: HTMLElement = document.querySelector('.minute-hand-container')!
  const secondHandContainer: HTMLElement = document.querySelector('.second-hand-container')!

  if (hours === 0) {
    hourHandContainer.style.setProperty('--i', '60')
    await sleep(600)
    hourHandContainer.style.setProperty('--t', '0s')
    hourHandContainer.style.setProperty('--i', '0')
    await sleep(1)
    hourHandContainer.style.setProperty('--t', '0.5s')
  } else {
    hourHandContainer.style.setProperty('--i', `${hours + minutes / 60}`)
  }

  if (minutes === 0) {
    minuteHandContainer.style.setProperty('--i', '60')
    await sleep(600)
    minuteHandContainer.style.setProperty('--t', '0s')
    minuteHandContainer.style.setProperty('--i', '0')
    await sleep(1)
    minuteHandContainer.style.setProperty('--t', '0.5s')
  } else {
    minuteHandContainer.style.setProperty('--i', `${minutes + seconds / 60}`)
  }

  if (seconds === 0) {
    secondHandContainer.style.setProperty('--i', '60')
    await sleep(600)
    secondHandContainer.style.setProperty('--t', '0s')
    secondHandContainer.style.setProperty('--i', '0')
    await sleep(1)
    secondHandContainer.style.setProperty('--t', '0.5s')
  } else {
    secondHandContainer.style.setProperty('--i', `${seconds}`)
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
  height: 75%;
  position: absolute;
  width: 1rem;

  transform: rotate(calc(1deg * 30 * var(--i)));
  transition-duration: var(--t);
}

.minute-hand-container {
  height: 85%;
  position: absolute;
  width: .5rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
  transition-duration: var(--t);
}

.second-hand-container {
  height: 95%;
  position: absolute;
  width: .5rem;

  transform: rotate(calc(1deg * 6 * var(--i)));
  transition-duration: var(--t);
}

.hour-hand {
  height: 50%;
  width: inherit;

  background-color: var(--green-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-3);
}

.minute-hand {
  height: 50%;
  width: inherit;

  background-color: var(--yellow-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-4);
}

.second-hand {
  height: 70%;
  width: inherit;

  background-color: var(--red-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-1);
}

.clock-center-hour {
  height: 1.5rem;
  position: absolute;
  width: 1.5rem;

  background-color: var(--green-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-3);
}

.clock-center-minute {
  height: 1rem;
  position: absolute;
  width: 1rem;

  background-color: var(--yellow-5);
  border-radius: var(--radius-round);
  box-shadow: var(--shadow-4);
}

.clock-center-second {
  height: 2.5rem;
  position: absolute;
  width: 2.5rem;

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
}
</style>

