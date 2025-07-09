<script setup>
import { ref, onMounted } from 'vue'

const projects = ref([])

onMounted(async () => {
  const response = await fetch(`${import.meta.env.VITE_API_URL}/projects/all`)
  projects.value = await response.json()
})
</script>

<template>
  <header>
    <small>Workshop Jenkins - customize as you wish</small>
  </header>

  <main>
    <h1>My first deployement... and Vue.js</h1>
    <section>
      <h2>Projects reminder:</h2>
      <ul>
        <li v-for="name in projects" :key="name">
          {{ name }}
        </li>
      </ul>
      <small>This is not exhaustive</small>
    </section>
  </main>
</template>