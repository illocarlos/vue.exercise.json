<script setup>

const ejemProp = defineProps({
    title: String,
    body: String,
    userId: {
        type: Number,
        default: "no hay num"
    },
})
</script>

<template>
    <div class="BC">
        <p :class="`text-${color}`">
            {{ title }} - {{ body }}-{{ id }}
        </p>
        <button @click="$emit('cambioEj', title)" class="btn">{{ userId }}</button>
    </div>
</template>



<style lang="scss">
@import "./Buttom.scss";
</style>