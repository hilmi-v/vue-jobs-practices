<script setup>
import { ref } from 'vue'

let i = ref(0)
function increment() {
  i.value++
}
</script>

<template>
  <button @click="increment" class="p-2 bg-green-700 text-white">
    {{ i }}
  </button>
</template>

<style></style>
