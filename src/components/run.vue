<template>
    <div class="run">
        <div class="run_pomo seed">
            <h1 data-animation="header">RUN PUMA</h1>
        </div>
        <div class="run_photogrid seed">
            <div class="img">
                <img
                    src="https://res.cloudinary.com/hdsdev/image/upload/c_scale,f_auto,g_center,h_1080,q_70/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Product-A_Deviate-Nitro-2-Wns_Q3_0005"
                    alt=""
                />
            </div>
            <div class="img">
                <img
                    src="https://res.cloudinary.com/hdsdev/image/upload/c_scale,f_auto,g_center,h_1080,q_70/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Deviate-Nitro-2-Mens_Q3_0365"
                    alt=""
                />
            </div>
            <div class="img">
                <img
                    src="https://res.cloudinary.com/hdsdev/image/upload/c_scale,f_auto,g_center,h_1080,q_70/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Product-A_Deviate-Nitro-2-Wns_Q3_0063"
                    alt=""
                />
            </div>
            <div class="img">
                <img
                    src="https://res.cloudinary.com/hdsdev/image/upload/c_scale,f_auto,g_center,h_1080,q_70/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Deviate-Nitro-2-Wns_Q3_0600"
                    alt=""
                />
            </div>
            <div class="img">
                <img
                    src="https://res.cloudinary.com/hdsdev/image/upload/c_scale,f_auto,g_center,h_1080,q_70/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Product-A_Deviate-Nitro-2-Mens_Q3_0106"
                    alt=""
                />
            </div>
            <div class="img">
                <img
                    src="https://res.cloudinary.com/hdsdev/image/upload/c_scale,f_auto,g_center,h_1080,q_70/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Product-A_Deviate-Nitro-2-Wns_Q3_0035"
                    alt=""
                />
            </div>
        </div>
        <div class="run_footer seed">
            <h1 data-animation="header">RUN PUMA</h1>
            <p data-animation="paragraph">
                The RUN PUMA line fits the needs of every runner. Providing you with innovative technology for your long distance runs or an
                ultra-lightweight design to challenge your tempo run’s performance. RUN PUMA is here to support you from the first mile on.
            </p>
            <button>SHOP THE COLLECTION</button>
        </div>
    </div>
</template>

<script setup>
import { IO } from "../animations/observe";
import { onMounted } from "vue";
import gsap from "gsap";
onMounted(() => {
    IO(document.querySelector(".run_pomo"), { threshold: 1 }).then(() => {
        document.querySelector(".run_pomo").classList.add("animate_zoom");
    });
    const wrap = document.querySelector(".run");
    let skew = 0;
    let sections = gsap.utils.toArray(".seed");
    let tl = gsap.timeline({
        scrollTrigger: {
            trigger: ".run",
            start: "top top",
            scrub: -1,
            toggleActions: "play reset none restart",
            end: "+=900",
            pinSpacer: false,
            pin: "body",
            onUpdate: (self) => {
                skew = self.getVelocity() / -100;
            },
        },
    });
    tl.to(sections, {
        x: -wrap.offsetWidth * 3,
        duration: 5,
        skewY: () => skew,
        ease: "power1.easeInOut",
    });
});
</script>

<style lang="scss">
.run {
    height: 100vh;
    display: flex;
    overflow: hidden;
    flex-wrap: nowrap;
    .seed {
        flex-shrink: 0;
    }

    &_pomo {
        height: 100%;
        @include flex_col(0);
        background-size: 110rem;
        background-attachment: fixed;
        background-repeat: no-repeat;
        background-image: url(https://res.cloudinary.com/hdsdev/image/upload/c_fill,f_auto,g_center,h_1080,q_70,w_1920/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Deviate-Nitro-2_Q3-Group_0896);
        align-items: center;
        justify-content: center;
        width: 100%;
        h1 {
            color: white;
            font-size: toRem(150);
        }
    }
    &_photogrid {
        width: 200%;
        @include flex(center, center, 0 3rem);
        padding: 3rem;
        .img {
            height: 100%;
            width: 100%;
            overflow: hidden;
            img {
                width: auto;
                height: 100%;
                min-width: 30rem;
                transition: scale 1s ease-in-out;
                &:hover {
                    scale: 1.2;
                }
            }
        }
    }
    &_footer {
        @include flex_col(2rem);
        width: 100%;
        background-size: 110rem;
        background-attachment: fixed;
        background-repeat: no-repeat;
        height: 100%;
        align-items: center;
        justify-content: center;
        background-color: rgba(0, 0, 0, 0.728);
        background-blend-mode: darken;
        background-image: url(https://res.cloudinary.com/hdsdev/image/upload/c_fill,f_auto,g_center,h_1080,q_70,w_1920/v1/campaign/nitro/img/22AW_RT_Run-PUMA_Deviate-Nitro-2_Q3-Group_0716);
        h1 {
            color: white;
            font-size: toRem(100);
        }
        p {
            width: 55%;
            color: white;
            text-align: center;
            font-size: toRem(25);
            line-height: 2.4rem;
        }
        button {
            background: #fb627c;
            color: white;
            padding: 1.5rem 3rem;
        }
    }
}
.animate_zoom {
    animation-name: zoom;
    animation-duration: 3s;
    animation-timing-function: ease-in-out;
    animation-fill-mode: forwards;
}

@keyframes zoom {
    0% {
        background-position-x: 0%;
    }
    100% {
        background-position-x: 100%;
        background-size: 100rem;
    }
}
</style>
