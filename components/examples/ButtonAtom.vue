<template>
    <div class="p-5 bg-dark border-rounded">
      <button @click="increment">Púlsame {{ count }}</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  const count = ref(0);
  
  function increment() {
    count.value++;

    emit('increment', count.value);
  }

  const emit = defineEmits(['increment'])
  </script>