<template>
    {{ textNumber }}
    <input-atom :text="myText" @update:value="myText = $event" />  
    <button-atom @increment="myNumber = $event" />    
</template>
  
<script setup>
    import { ref,computed } from 'vue'
    import ButtonAtom from './ButtonAtom.vue';  

    const myText= ref('');
    const myNumber= ref(0);
    const textNumber= computed(() => myText.value + ' ' + myNumber.value);
   
</script>