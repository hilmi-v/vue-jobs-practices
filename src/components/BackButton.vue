<script setup>
import { RouterLink } from 'vue-router'
</script>
<template>
  <section class="container px-12 py-10 m-auto">
    <RouterLink class="text-green-700 hover:text-green-900" to="/">
      <span class="mr-2 pi pi-arrow-circle-left"></span> back to jobs list
    </RouterLink>
  </section>
</template>
