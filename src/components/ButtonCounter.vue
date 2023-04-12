<script setup>
  import { ref } from 'vue'
  defineProps(['title', 'name', 'colorText'])
   const counter = ref(0)
   const incremento = () => {
     counter.value++
   }
</script>
<template>
  <h2>{{ title }}</h2>
  <h3>{{ name }}</h3>
  <button @click="incremento" class="btn" :class="`btn-${colorText}`">Counter {{ counter }}</button>
</template>