<script setup>
import King from './components/King.vue';
import { kings } from './datos'
import { ref } from 'vue'

const counter = ref(0)
const kingsCount = kings.length

const nextKing = () => {
  counter.value++
  if (counter.value === kingsCount) {
    counter.value = 0
  }
}
</script>

<template>
  <main>
    <King :kingNumber='counter' />
    <button @click="nextKing">Siguiente ({{ `${counter + 1}/${kingsCount}` }})</button>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
button {
  font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
    Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
    font-size: 1rem;
    padding: 0.25rem 0.75rem;
}
</style>
