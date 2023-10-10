<template>
    <div class="bg-slate-700 pb-2">
      <div class="max-w-sm rounded overflow-hidden shadow-lg border-white">
        <img class="w-full h-[70px]" :src="image" :alt="name">
        <div class="px-6 py-2 text-center">
          <div class="font-bold text-xl mb-2">{{name}}</div>    
        </div>
        <div class="px-6 text-center">
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">{{from}} - {{ toFormatted }}</span>    
        </div>
      </div>
    </div>
</template>

<script setup>

import { computed } from 'vue'

const props = defineProps({
    image: {
        type: String,
    },
    name: {
        type: String,        
    },
    from: {
        type: Number,        
    },
    to: {
        type: Number,        
    },    
})

const toFormatted = computed(() => {
    return (props.to === 0) ? '?' : props.to 
})

</script>