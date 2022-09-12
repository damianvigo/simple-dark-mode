<script setup>
import { ref } from 'vue';


// On page load or when changing themes, best to add inline in `head` to avoid FOUC
if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
  document.documentElement.classList.add('dark')
} else {
  document.documentElement.classList.remove('dark')
}

// // Whenever the user explicitly chooses light mode
// localStorage.theme = 'light'

// // Whenever the user explicitly chooses dark mode
// localStorage.theme = 'dark'

// // Whenever the user explicitly chooses to respect the OS preference
// localStorage.removeItem('theme')

const toggleDarkMode = ref(document.documentElement.className === 'dark')

const changeDarkMode = () => {
  // console.log(toggleDarkMode)
  toggleDarkMode.value = document.documentElement.classList.toggle('dark');
  toggleDarkMode.value ? localStorage.theme = 'dark' : localStorage.theme = 'light'
}

</script>

<template >
  <main class="container mx-auto">
    <h1 class="text-center text-4xl dark:bg-gray-800 dark:text-white py-20">Dark mode</h1>
    <div class="text-center">
      <button class="bg-gray-700 text-white rounded-xl py-3 px-4" @click="changeDarkMode">Dia/Noche
        {{toggleDarkMode}}</button>

    </div>
    <br>
  </main>
</template>

<style>
/* body {
  background: #202020;
} */
</style>