<script setup>
import { defineProps } from 'vue'

defineProps({
  title: {
    type: String,
    default: 'Search Job for Jobless',
  },
  subTitle: {
    type: String,
    default: 'Kerja, Kerja, Kerja',
  },
})
</script>

<template>
  <section class="h-[80vh] w-screen overflow-hidden relative">
    <img
      src="https://bairesdev.mo.cloudinary.net/blog/2023/09/How-Many-Web-Developers-in-the-World-1.jpg?tx=w_1920,q_auto"
      alt="hero"
      class="object-cover w-full h-full"
    />
    <div
      class="h-[80vh] w-screen absolute top-0 left-0 bg-green-500 bg-opacity-40"
    ></div>

    <div
      class="absolute text-center text-white transform -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
    >
      <h1 class="mb-2 font-bold text-7xl">{{ title }}</h1>
      <h2 class="text-2xl font-bold">{{ subTitle }}</h2>
    </div>
  </section>
</template>
