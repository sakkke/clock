<script setup lang="ts">
import Clock from './components/Clock.vue'
</script>

<template>
  <Clock />
</template>

<style>
@import 'open-props/style';
@import 'open-props/normalize';

body {
  display: grid;
  place-items: center;

  background-image: var(--gradient-29);
}

@media (prefers-color-scheme: dark) {
  body {
    background-image: var(--gradient-23);
  }
}
</style>

