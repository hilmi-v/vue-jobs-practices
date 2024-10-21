<script setup>
import { ref, defineProps, computed } from 'vue'
import { RouterLink } from 'vue-router'

const prop = defineProps({
  job: {
    type: Object,
  },
})

const showFullDescription = ref(false)

const toggleShowFullDescription = () => {
  showFullDescription.value = !showFullDescription.value
}

const truncatedDesc = computed(() => {
  let description = prop.job.description
  if (!showFullDescription.value) {
    description = description.substring(0, 90) + '...'
  }
  return description
})
</script>

<template>
  <div class="flex flex-col p-4 mb-2 bg-white rounded-lg shadow-md w-80">
    <p class="mb-1 text-sm">{{ job.type }}</p>
    <h3 class="mb-2 text-xl font-bold">{{ job.title }}</h3>
    <div class="mb-2">
      <p class="mb-1 text-sm text-gray-700">
        {{ truncatedDesc }}
      </p>
      <button
        class="text-sm text-green-400 hover:text-green-600"
        @click="toggleShowFullDescription"
      >
        {{ showFullDescription ? 'less' : 'more' }}
      </button>
    </div>
    <p class="mb-2 text-sm text-green-400">{{ job.salary }} / Year</p>
    <hr />
    <div class="flex flex-col items-center justify-between mt-2 md:flex-row">
      <p class="mb-2 text-sm text-orange-800">
        <span class="pi pi-map-marker"></span>
        {{ job.location }}
      </p>
      <RouterLink
        :to="'jobs/' + job.id"
        class="self-end w-full p-1 text-center text-white bg-green-500 rounded-lg shadow md:w-28 hover:bg-green-600"
      >
        read more
      </RouterLink>
    </div>
  </div>
</template>
