<template>
    <div class="feature_wrap">
        <div class="feature_wrap_txt">
            <h2 class="text" data-animation="header">{{ data[rhyme].name }}</h2>
            <p class="text" data-animation="paragraph">{{ data[rhyme].name }}</p>
            <div class="btn">
                <button>Shop men's</button>
                <button>shop women's</button>
            </div>
        </div>
        <div class="feature_wrap_imgScroller">
            <div v-for="re in data" :key="re._id" class="img_sect">
                <img :src="re.imgsrc" alt="" />
            </div>
        </div>
        <div class="feature_wrap_mode">
            <img @click="change(rhyme + -1)" :disabled="rhyme <= 0" :class="{ red: rhyme <= 0 }" class="ass" src="../assets/left.svg" alt="" />
            <div class="feature_wrap_mode_robo">
                <img @click="change(re._id)" :class="{ zoom: re._id == rhyme }" v-for="re in data" :key="re._id" :src="re.imgsrc" alt="" />
            </div>
            <img
                @click="change(rhyme + 1)"
                :disabled="rhyme >= data.length - 1"
                :class="{ red: rhyme >= data.length - 1 }"
                style="transform: rotateY(180deg)"
                class="ass"
                src="../assets/left.svg"
                alt=""
            />
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";
import data from "../db/data.json";
import gsap from "gsap";
const rhyme = ref(0);

const change = (val) => {
    document.querySelectorAll(".feature_wrap_txt .text").forEach((item) => {
        item.classList.toggle("disappear");
    });
    setTimeout(() => {
        document.querySelectorAll(".feature_wrap_txt .text").forEach((item) => {
            item.classList.toggle("disappear");
        });
    }, 300);
    setTimeout(() => {
        rhyme.value = val;
        const container = document.querySelector(".feature_wrap_imgScroller");
        const element = document.querySelector(`.img_sect:nth-child(${rhyme.value + 1})`);
        const distance = element.offsetLeft - container.offsetLeft;

        gsap.to(container, {
            duration: 1,
            scrollLeft: distance,
            ease: "circ.easeInOut",
        });
    }, 200);
};
</script>

<style lang="scss">
.feature_wrap {
    position: relative;
    &_txt {
        position: absolute;
        left: 10%;
        top: 30%;
        width: 25%;
        @include flex_col(0.8rem);
        h2 {
            font-size: toRem(33);
            font-weight: 500;
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
        overflow-x: hidden;
        flex-wrap: nowrap;
        gap: 0 5rem;
        cursor: pointer;
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
.red {
    cursor: not-allowed !important;
    pointer-events: none !important;
}
.disappear {
    opacity: 0;
    transition: 0.2s ease-in-out;
}
</style>
