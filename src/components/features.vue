<template>
    <div class="feature_wrap">
        <div class="feature_wrap_txt">
            <h2 data-animation="header">{{ data[rhyme].name }}</h2>
            <p data-animation="paragraph">{{ data[rhyme].name }}</p>
            <div class="btn">
                <button>Shop men's</button>
                <button>shop women's</button>
            </div>
        </div>
        <div class="feature_wrap_imgScroller">
            <div v-for="re in data" :key="re._id" :class="{ current: re._id == rhyme }" class="img_sect">
                <img :src="re.imgsrc" alt="" />
            </div>
        </div>
        <div class="feature_wrap_mode">
            <img class="ass" src="../assets/left.svg" alt="" />
            <div class="feature_wrap_mode_robo">
                <img @click="change(re._id)" :class="{ zoom: re._id == rhyme }" v-for="re in data" :key="re._id" :src="re.imgsrc" alt="" />
            </div>
            <img style="transform: rotateY(180deg)" class="ass" src="../assets/left.svg" alt="" />
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";
import data from "../db/data.json";
import gsap from "gsap";
const rhyme = ref(0);

const change = (val) => {
    rhyme.value = val;
    const container = document.querySelector(".feature_wrap_imgScroller");
    const element = document.querySelector(".current");
    const distance = element.offsetLeft - container.offsetLeft;
    gsap.to(container, {
        duration: 1, // Animation duration in seconds
        scrollLeft: distance, // Scroll position to animate to
        ease: "power1.out", // Easing function to use (optional)
    });
};
</script>

<style lang="scss">
.feature_wrap {
    position: relative;
    &_txt {
        position: absolute;
        left: 10%;
        top: 30%;
        width: 23%;
        @include flex_col(0.8rem);
        h2 {
            font-size: toRem(30);
            color: $blacktxt;
        }
        p {
            font-size: toRem(19);
            line-height: 1.5rem;
        }
        .btn {
            margin-top: 1.5rem;
            @include flex_col(1rem);
            button {
                display: block;
                text-transform: capitalize;
                padding: 1.1rem 1.5rem;
                font-size: 1em;
                background: #ae946d;
                color: white;
            }
        }
    }
    &_imgScroller {
        display: flex;
        overflow-x: auto;
        flex-wrap: nowrap;
        gap: 0 5rem;
        scroll-snap-type: x mandatory;
        -webkit-overflow-scrolling: touch;
        .img_sect {
            width: 100vw;
            flex-shrink: 0;
            display: flex;
            align-items: center;
            justify-content: flex-end;
            img {
                width: 60%;
            }
        }
    }
    &_mode {
        width: 80%;
        left: 10%;
        position: absolute;
        @include flex(space-evenly, center, 5rem);
        top: 80%;
        .ass {
            cursor: pointer;
        }
        &_robo {
            @include flex(center, center, 0 2rem);
            width: 4rem;
            img {
                width: 100%;
                transition: transform 0.5s ease-out;
                opacity: 0.5;
                -webkit-user-drag: none;
                cursor: pointer;
            }
        }
    }
}
.zoom {
    transform: scale(1.5);
    opacity: 1 !important;
}
</style>
