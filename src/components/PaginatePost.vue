<script setup>
defineProps(['inicio', 'fin', 'maxLength'])
</script>
<template>
  <div class="btn-group" role="group" aria-label="Basic outlined example">
    <button type="button" class="btn btn-outline-primary" @click="$emit('anterior')" :disabled="inicio <= 0">Anterior</button>
    <button type="button" class="btn btn-outline-primary" @click="$emit('siguiente')" :disabled="fin >= maxLength">Siguiente</button>
  </div>
</template>