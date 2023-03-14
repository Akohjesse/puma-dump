<script setup>
import Scene from "./components/scene.vue";
import Feature from "./components/features.vue";
import Run from "./components/run.vue";
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
        <Run />
    </div>
</template>

<style scoped></style>
