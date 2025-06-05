<template>
  <div>
    <header class="flex flex-row w-full items-center justify-between p-4 bg-green-400 border-b-2 max-sm:flex-col max-sm:items-start">
      <div class="flex basis-1/4 items-center justify-start px-8 min-w-40 max-sm:basis-auto max-sm:px-0 max-sm:w-full max-sm:justify-between">
        <img src="/assets/img/loogo_comand.png" alt="Logo" class="w-16 h-16" />
        <div class="sm:hidden cursor-pointer" @click="switchBurger">
          <i v-if="!burger" class="fas fa-bars fa-lg"></i> 
          <i v-else class="fas fa-times fa-lg"></i>        
        </div>
      </div>

      <nav class="hidden sm:flex flex-row gap-4">
        <NuxtLink to="/" class="p-2 hover:bg-green-600 hover:text-white rounded">Home</NuxtLink>
        <div class="relative">
          <NuxtLink to="#" @click.prevent="toggleLabs" class="p-2 hover:bg-green-600 hover:text-white rounded">Labs</NuxtLink>
          <ul v-show="labsOpen" class="absolute bg-white border mt-2 rounded shadow-lg z-10">
            <li><NuxtLink to="/Lab4" class="block p-2 hover:bg-green-600 hover:text-white">Lab4</NuxtLink></li>
            <li><NuxtLink to="/Lab5" class="block p-2 hover:bg-green-600 hover:text-white">Lab5</NuxtLink></li>
            <li><NuxtLink to="/Lab6" class="block p-2 hover:bg-green-600 hover:text-white">Lab6</NuxtLink></li>
          </ul>
        </div>
        <NuxtLink to="/login" class="p-2 hover:bg-green-600 hover:text-white rounded">LogIn</NuxtLink>
        <NuxtLink to="/logout" class="p-2 hover:bg-green-600 hover:text-white rounded">LogOut</NuxtLink>
      </nav>
    </header>

    <!-- Мобильное меню -->
    <nav v-show="burger" class="flex flex-col gap-0 bg-white border-b-2 sm:hidden">
      <NuxtLink to="/" class="p-4 hover:bg-green-400 hover:text-white border-t">Home</NuxtLink>
      <div class="border-t">
        <NuxtLink to="#" @click.prevent="toggleLabs" class="p-4 hover:bg-green-400 hover:text-white block">Labs</NuxtLink>
        <ul v-show="labsOpen" class="bg-gray-100 pl-4">
          <li><NuxtLink to="/Lab4" class="block p-3 hover:bg-green-400 hover:text-white border-t">Lab4</NuxtLink></li>
          <li><NuxtLink to="/Lab5" class="block p-3 hover:bg-green-400 hover:text-white border-t">Lab5</NuxtLink></li>
          <li><NuxtLink to="/Lab6" class="block p-3 hover:bg-green-400 hover:text-white border-t">Lab6</NuxtLink></li>
        </ul>
      </div>
      <NuxtLink to="/login" class="p-4 hover:bg-green-400 hover:text-white border-t">LogIn</NuxtLink>
      <NuxtLink to="/logout" class="p-4 hover:bg-green-400 hover:text-white border-t">LogOut</NuxtLink>
    </nav>

    <main class="p-8 max-sm:p-4">
      <slot />
    </main>

    <footer class="flex flex-row w-full bg-purple-700 border-t-2 border-gray-400 items-center px-4 py-2 gap-4">
      <a href="#"><img src="https://www.google.com/favicon.ico" class="w-6 h-6" /></a>
      <a href="#"><img src="https://github.com/favicon.ico" class="w-6 h-6" /></a>
      <a href="#"><img src="https://netlify.com/favicon.ico" class="w-6 h-6" /></a>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const labsOpen = ref(false);
const burger = ref(false);

const toggleLabs = () => {
  labsOpen.value = !labsOpen.value;
};

const switchBurger = () => {
  burger.value = !burger.value;
};

useHead({
  script: [
    {
      src: "https://kit.fontawesome.com/67d2ef7984.js",
      crossorigin: "anonymous",
      async: true
    },
    {
      src: "https://www.googletagmanager.com/gtag/js?id=G-RES3C5BQ23",
      async: true
    },
    {
      children: `
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-RES3C5BQ23');
      `,
      type: "text/javascript"
    }
  ]
});
</script>
