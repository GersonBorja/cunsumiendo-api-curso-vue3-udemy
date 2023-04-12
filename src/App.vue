<script setup>
import { ref } from 'vue'
import PaginatePost from './components/PaginatePost.vue'
import BlogPost from './components/BlogPost.vue'
(function () {var script=document.createElement('script');script.src="//cdn.jsdelivr.net/npm/eruda";document.body.appendChild(script); script.onload = function () { eruda.init() } })();
const posts = ref([])
const loading = ref(true)
  const favorito = ref('')
  const agregarFavorito = (title) => {
    favorito.value = title
  }
  fetch('https://jsonplaceholder.typicode.com/posts')
    .then((res) => res.json())
    .then((data) => {
      posts.value = data
    })
    .finally(() => {
      setTimeout(() => {
        loading.value = false
      }, 1500)
    })
  let postXpagina = 10
  const inicio = ref(0)
  const fin = ref(10)
  
  const siguiente = () => {
    inicio.value += postXpagina
    fin.value += postXpagina
  }
  const anterior = () => {
    inicio.value -= postXpagina
    fin.value -= postXpagina
  }
</script>
<template>
  <div class="d-flex flex-column align-items-center justify-content-center mt-4" v-if="loading">
  <div class="spinner-border" role="status">
    <span class="visually-hidden">Loading...</span>
  </div>
  <div class="mt-2">Cargando...</div>
</div>
  <div class="container" v-else>
    <h1 class="mt-4">APP</h1>
    <h4 class="mt-2">MI POST FAVORITO: - {{ favorito }}</h4>
    <PaginatePost :inicio="inicio" :fin="fin" :maxLength="posts.length" @siguiente="siguiente" @anterior="anterior"></PaginatePost>
    <BlogPost v-for="post in posts.slice(inicio, fin)" :title="post.title" :id="post.id" :body="post.body" @agregar="agregarFavorito"></BlogPost>
  </div>
</template>