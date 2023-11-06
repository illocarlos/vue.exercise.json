<script setup>
// esta es una buena forma de tener las funcions que llamamos desde el padre paandola como propsç
// si la llamamos asi no tenemos que usar en los botones el simbolo "$emit"solo emit
// const emit = defineEmits(['btNext'], ['btBack'])
defineProps(['inicioPage', 'finPage', 'maxArray'])



</script>
<template>
    <div class="bl-btn">
        <button :disabled="inicioPage === 0" @click="$emit('btBack')" class="btn-back">back-{{ inicioPage }}</button>
        <button :disabled="finPage > maxArray" @click="$emit('btNext')" class="btn-next">next-{{ finPage }}</button>
    </div>
</template>

<style lang="scss">
@import './Paginacion';
</style>