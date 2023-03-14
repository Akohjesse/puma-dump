<script setup>
import Scene from "./components/scene.vue";
import Feature from "./components/features.vue";
import { split } from "./animations/text";
import { onMounted } from "vue";

onMounted(() => {
    split();
});
</script>

<template>
    <div>
        <Scene />
        <Feature />
    </div>
</template>

<style scoped></style>
