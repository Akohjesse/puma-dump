<template>
  <div class="scene_wrap">
         <canvas :width="r.innerWidth" :height="r.innerHeight" id="scene"></canvas>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';

const r = window;

onMounted(() => {
    const html = document.documentElement;
        const canvas = document.getElementById("scene");
        const context = canvas.getContext("2d");
        const frameCount = 208;
        const currentFrame = (index) => {
            return `/src/assets/scene/ezgif-frame-${index.toString().padStart(3, "0")}.png`;
        };

        const img = new Image();
        img.src = currentFrame(1);
        img.onload = function () {
            context.drawImage(img, 0, 0, canvas.width, canvas.height);
        };

        const preloadImages = () => {
            for (let i = 0; i < frameCount; i++) {
                const img = new Image();
                img.src = currentFrame(i);
            }
        };

        const wrap = document.querySelector(".scene_wrap");
        window.addEventListener("scroll", () => {
            const scrollTop = html.scrollTop - wrap.offsetTop;
            const maxScrollTop = wrap.scrollHeight - window.innerHeight;
            const scrollFraction = scrollTop / maxScrollTop;
            const frameIndex = Math.min(frameCount - 1, Math.floor(scrollFraction * frameCount));
            if (frameIndex > 0) {
                requestAnimationFrame(() => updateImage(frameIndex + 1));
            }
        });

        const updateImage = (index) => {
            img.src = currentFrame(index);
            context.drawImage(img, 0, 0, canvas.width, canvas.height);
        };

        preloadImages();
})
</script>

<style lang="scss">
.scene_wrap{
    color: white;
    height: 1000vh;
    position: relative;
    canvas {
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        max-width: 100vw;
        max-height: 100vh;
        position: sticky;
    }
}
</style>