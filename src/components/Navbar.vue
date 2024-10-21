<script setup>
import logo from '@/assets/logo.svg'
import hamburger from '@/assets/hamburger.svg'
import { RouterLink, useRoute } from 'vue-router'
let show = () => {
  let navbar = document.getElementById('navbar-links')
  navbar.classList.toggle('hidden')
}

const isActive = routePath => {
  let route = useRoute()
  return route.path === routePath
}
</script>

<template>
  <nav
    class="sticky top-0 z-[999] flex flex-wrap items-center justify-between py-2 bg-green-700 w-dvw px-7"
  >
    <RouterLink to="/" class="flex items-center ms-4">
      <img :src="logo" alt="logo" class="w-5 lg:w-10" />
      <h1 class="text-xl font-bold text-white lg:text-3xl">Job for Jobless</h1>
    </RouterLink>
    <button @click="show">
      <img :src="hamburger" alt="" class="w-7 me-8 lg:hidden" />
    </button>
    <ul
      id="navbar-links"
      class="flex-col justify-center hidden w-full gap-4 mx-auto mt-4 font-semibold text-white lg:flex me-10 lg:flex-row lg:w-auto lg:mt-0"
    >
      <RouterLink
        class="flex justify-center p-1 px-2 m-2 rounded"
        :class="[isActive('/') ? 'bg-green-800' : 'hover:bg-green-800']"
        to="/"
        >Home</RouterLink
      >
      <RouterLink
        class="flex justify-center p-1 px-2 m-2 rounded"
        :class="[isActive('/jobs') ? 'bg-green-800' : 'hover:bg-green-800']"
        to="/jobs"
      >
        Jobs</RouterLink
      >
      <RouterLink
        class="flex justify-center p-1 px-2 m-2 rounded"
        :class="[isActive('/jobs/add') ? 'bg-green-800' : 'hover:bg-green-800']"
        to="/jobs/add"
        >Add Jobs</RouterLink
      >
    </ul>
  </nav>
</template>
