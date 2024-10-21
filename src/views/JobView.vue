<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'
import { RouterLink, useRoute } from 'vue-router'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'
import BackButton from '@/components/BackButton.vue'

const loading = ref(true)
const job = ref()
const route = useRoute()
const jobId = route.params.id
onMounted(async () => {
  try {
    const res = await axios.get(`/api/jobs/${jobId}`)
    job.value = await res.data
    console.log(job.value)
    // const res = await fetch(`/api/jobs/${jobId}`)
    // job.value = await res.json()
  } catch (err) {
    console.error(err)
  } finally {
    loading.value = false
  }
})
</script>

<template>
  <BackButton></BackButton>
  <div class="flex items-center justify-center w-full" v-if="loading">
    <PulseLoader class="mx-auto text-7xl" />
  </div>
  <section class="bg-green-50" v-else>
    <div class="container px-6 py-10 m-auto">
      <div class="grid w-full grid-cols-1 gap-6 md:grid-cols-70/30">
        <main>
          <div
            class="p-6 text-center bg-white rounded-lg shadow-md md:text-left"
          >
            <div class="mb-4 text-gray-500">{{ job.type }}</div>
            <h1 class="mb-4 text-3xl font-bold">{{ job.title }}</h1>
            <div
              class="flex justify-center mb-4 text-gray-500 align-middle md:justify-start"
            >
              <i class="mr-2 text-lg text-orange-700 pi pi-map-marker"></i>
              <p class="text-orange-700">{{ job.location }}</p>
            </div>
          </div>

          <div class="p-6 mt-6 bg-white rounded-lg shadow-md">
            <h3 class="mb-6 text-lg font-bold text-green-800">
              Job Description
            </h3>

            <p class="mb-4">
              {{ job.description }}
            </p>

            <h3 class="mb-2 text-lg font-bold text-green-800">Salary</h3>

            <p class="mb-4">{{ job.salary }} / Year</p>
          </div>
        </main>

        <!-- Sidebar -->
        <aside>
          <!-- Company Info -->
          <div class="p-6 bg-white rounded-lg shadow-md">
            <h3 class="mb-6 text-xl font-bold">Company Info</h3>

            <h2 class="text-2xl">{{ job.company.name }}</h2>

            <p class="my-2">
              {{ job.company.description }}
            </p>

            <hr class="my-4" />

            <h3 class="text-xl">Contact Email:</h3>

            <p class="p-2 my-2 font-bold">
              {{ job.company.contactEmail }}
            </p>

            <h3 class="text-xl">Contact Phone:</h3>

            <p class="p-2 my-2 font-bold">
              {{ job.company.contactPhone }}
            </p>
          </div>

          <!-- Manage -->
          <div class="p-6 mt-6 bg-white rounded-lg shadow-md">
            <h3 class="mb-6 text-xl font-bold">Manage Job</h3>
            <RouterLink
              :to="`/jobs/edit/${job.id}`"
              class="block w-full px-4 py-2 mt-4 font-medium text-center text-white bg-green-500 rounded-lg hover:bg-green-600 focus:outline-none focus:shadow-outline"
              >Edit Job</RouterLink
            >
            <RouterLink
              class="block w-full px-4 py-2 mt-4 font-medium text-center text-white bg-red-500 rounded-lg hover:bg-red-600 focus:outline-none focus:shadow-outline"
            >
              Delete Job
            </RouterLink>
          </div>
        </aside>
      </div>
    </div>
  </section>
</template>
