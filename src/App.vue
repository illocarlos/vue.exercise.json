<script setup>
import { ref } from 'vue';
import BC from "./components/Buttom/BC.vue"
import Paginacion from './components/Paginacion/Paginacion.vue';

const arrayPost = ref([])

fetch('https://jsonplaceholder.typicode.com/posts')
  .then(res => res.json())
  .then(data => arrayPost.value = data)


let cambio = ref("")
const cambioEj = (title) => {
  cambio.value = title
}
</script>

<template>
  <h1> mi fav es: {{ cambio }}</h1>
  <Paginacion />
  <BC v-for="ejem in arrayPost" :key="ejem.id" :title="ejem.title" :body="ejem.body" :userId="ejem.userId"
    @cambioEj="cambioEj">
  </BC>
</template>

<style lang="scss">
@import "./_App.scss";
</style>
