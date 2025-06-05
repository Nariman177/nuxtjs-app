<template>
  <div class="relative min-h-screen">
    <!-- Фоновая картинка -->
    <div 
      class="absolute inset-0 bg-cover bg-center z-0"
      :style="{ backgroundImage: 'url(assets/img/dolina.jpg)' }"
    ></div>
    
    <!-- Затемнение фона для лучшей читаемости текста -->
    <div class="absolute inset-0 bg-black bg-opacity-40 z-0"></div>
    
    <!-- Контент -->
    <div class="relative z-10 p-8 text-white">
      <h1 class="text-4xl font-bold mb-6">Home Page</h1>
      <p class="text-xl max-w-lg">Welcome to the home page!</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const showImage = ref(false);
</script>
