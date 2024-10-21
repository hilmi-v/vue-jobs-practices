<script setup>
import { onMounted, ref, defineProps } from 'vue'
import JobListing from './JobListing.vue'
import { RouterLink } from 'vue-router'
import axios from 'axios'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'

const jobs = ref([])
const loading = ref(true)
defineProps({
  showButton: {
    type: Boolean,
    default: false,
  },
  limit: {
    type: Number,
  },
})

onMounted(async () => {
  try {
    const res = await axios.get('/api/jobs')
    jobs.value = res.data
  } catch (err) {
    console.error(err)
  } finally {
    loading.value = false
  }
})
</script>

<template>
  <section class="bg-gray-100 w-dvw py-7">
    <h2 class="text-3xl font-bold text-center text-green-400 mb-7">Jobs</h2>
    <div class="flex items-center justify-center w-full" v-if="loading">
      <PulseLoader class="mx-auto text-7xl" />
    </div>
    <div class="flex flex-wrap justify-center gap-4 mx-auto" v-else>
      <JobListing
        v-for="job in jobs.slice(0, limit || jobs.length)"
        :key="job.id"
        :job="job"
      />
    </div>
    <div
      class="flex items-center justify-center max-w-lg mx-auto pt-7"
      v-show="showButton"
    >
      <RouterLink
        to="/jobs"
        class="px-24 py-2 text-base font-medium text-center text-white bg-gray-600 rounded-lg hover:bg-gray-700"
      >
        View All Jobs
      </RouterLink>
    </div>
  </section>
</template>
