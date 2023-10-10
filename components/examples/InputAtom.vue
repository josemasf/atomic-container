<template>
  <input
    type="text"
    :value="text"
    @input="$emit('update:value', $event.target.value)"
  />
</template>

<script setup>
    defineProps(['text'])
    defineEmits(['update:value'])
</script>
