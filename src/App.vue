<script setup>
import { ref } from 'vue';
import BC from "./components/Buttom/BC.vue"
import Paginacion from './components/Paginacion/Paginacion.vue';

const arrayPost = ref([])
const sumaPage = 7
const inicioPage = ref(0)
const finPage = ref(sumaPage)

fetch('https://jsonplaceholder.typicode.com/posts')
  .then(res => res.json())
  .then(data => arrayPost.value = data)


let cambio = ref("")
const cambioEj = (title) => {
  cambio.value = title
}

const btNext = () => {
  inicioPage.value = inicioPage.value + sumaPage
  finPage.value = finPage.value + sumaPage
}
const btBack = () => {
  inicioPage.value = inicioPage.value - sumaPage
  finPage.value = finPage.value - sumaPage
}
</script>

<template>
  <h1> mi fav es: {{ cambio }}</h1>
  <Paginacion @btNext="btNext" @btBack="btBack" />
  <BC v-for="ejem in arrayPost.slice(inicioPage, finPage)" :key="ejem.id" :title="ejem.title" :body="ejem.body"
    :userId="ejem.userId" @cambioEj="cambioEj">
  </BC>
</template>

<style lang="scss">
@import "./_App.scss";
</style>
