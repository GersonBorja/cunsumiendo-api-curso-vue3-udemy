<script setup>
  
  defineProps({
    title: String,
    id: Number,
    body: {
      type: String,
      default: 'Sin Descripción'
    }
  })
</script>
<template>
  <div class="card mt-4 p-4">
    <div class="body-card">
      <h5 class="card-title">{{ id }} - {{ title }}</h5>
      <p class="card-text">{{ body }}</p>
      <button class="btn btn-outline-primary" @click="$emit('agregar', title)">Agregar Favoritos</button>
    </div>
  </div>
</template>