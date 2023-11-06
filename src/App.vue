<script setup>
import { ref, computed } from 'vue';
import BC from "./components/Buttom/BC.vue"
import Paginacion from './components/Paginacion/Paginacion.vue';
import Loading from './components/loading/loading.vue'


const arrayPost = ref([])
const sumaPage = 7
const inicioPage = ref(0)
const finPage = ref(sumaPage)
const maxArray = computed(() => arrayPost.value.length)
const loading = ref(true)


fetch('https://jsonplaceholder.typicode.com/posts')
  .then(res => res.json())
  .then(data => arrayPost.value = data)
  .finally(() => {
    //esto es una manera de forzar que salga el load pero no se puede hacer 
    //el set es para demorar la carga de forma manual
    setTimeout(() => {
      loading.value = false
    }, 3000)
  })

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
  <loading v-if="loading" />

  <div v-else="loading">
    <Paginacion :maxArray="maxArray" :inicioPage="inicioPage" :finPage="finPage" @btNext="btNext" @btBack="btBack" />
    <BC v-for="ejem in arrayPost.slice(inicioPage, finPage)" :key="ejem.id" :title="ejem.title" :body="ejem.body"
      :userId="ejem.userId" @cambioEj="cambioEj">
    </BC>
  </div>
</template>

<style lang="scss">
@import "./_App.scss";
</style>
