<script setup>
import Card from '@/components/Card.vue'
import { RouterLink } from 'vue-router'
</script>

<template>
  <section class="grid grid-cols-1 gap-4 p-6 px-20 mt-2 md:grid-cols-2 w-dvw">
    <Card>
      <h2 class="text-2xl font-bold">For Developers</h2>
      <p class="mb-2 text-sm font-medium">Lorem, ipsum dolor.</p>
      <RouterLink to="/jobs" class="px-2 py-1 text-white bg-gray-700 rounded">
        browse jobs
      </RouterLink>
    </Card>
    <Card bgColor="bg-green-200">
      <h2 class="text-2xl font-bold">For Employers</h2>
      <p class="mb-2 text-sm font-medium">Lorem, ipsum dolor.</p>
      <RouterLink
        to="jobs/add"
        class="px-2 py-1 text-white bg-green-700 rounded"
        >add job</RouterLink
      >
    </Card>
  </section>
</template>
