<script setup>
import { onMounted, reactive, ref } from 'vue';
const planets = reactive({
  results: [],
  next: null,
  previous: null,
  count: 0
})
onMounted(() => {
  console.log('Component mounted')
  fetch('https://swapi.dev/api/planets')
    .then(response => response.json())
    .then(json => {
      planets.results = json.results
      planets.next = json.next
      planets.previous = json.previous
      planets.count = json.count
    })
})

</script>

<template>
  <h1>
    Hello World
  </h1>
  <ul>
    <li v-for="planet in planets.results" :key="planet.name">
      {{ planet.name }}
    </li>
  </ul>
</template>

<style scoped></style>
