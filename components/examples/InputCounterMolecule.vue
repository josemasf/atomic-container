<template>
    {{ myText }}
    <input-atom :text="myText" @update:value="myText = $event" />  
    <button-atom />    
</template>
  
<script setup>
    import { ref } from 'vue'
    
    import ButtonAtom from './ButtonAtom.vue';  

    const myText= ref('');
</script>