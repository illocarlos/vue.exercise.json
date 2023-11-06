<script setup>
</script>
<template>
    <div class="bl-btn">
        <button @click="$emit('btBack')" class="btn-back">back</button>
        <button @click="$emit('btNext')" class="btn-next">next</button>
    </div>
</template>

<style lang="scss">
@import './Paginacion';
</style>