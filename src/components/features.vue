<template>
    <div class="feature_wrap">
        <div class="feature_wrap_txt">
             <h2 data-animation="header">Deviate NITRO 2</h2>
             <p data-animation="paragraph">Max cushioning with improved efficiency for long runs.</p>
             <div class="btn">
                <button>Shop men's</button>
                <button>shop women's</button>
             </div>
        </div>
           <div class="feature_wrap_imgScroller">
                <div class="img_sect">
                    <img src="https://res.cloudinary.com/hdsdev/image/upload/c_fill,f_auto,g_center,h_800,q_60,w_800/v1/shoe_finder/products/376807_03_sv01" alt="">
                </div>
                <div class="img_sect">
                    <img src="https://res.cloudinary.com/hdsdev/image/upload/c_fill,f_auto,g_center,h_800,q_60,w_800/v1/shoe_finder/products/195504_02_sv01" alt="">
                </div>
                <div class="img_sect">
                    <img src="https://res.cloudinary.com/hdsdev/image/upload/c_fill,f_auto,g_center,h_800,q_60,w_800/v1/shoe_finder/products/Magnify-NITRO_mens_195170_09_sv01" alt="">
                </div>
                <div class="img_sect">
                    <img src="https://res.cloudinary.com/hdsdev/image/upload/c_fill,f_auto,g_center,h_800,q_60,w_800/v1/shoe_finder/products/Deviate-NITRO-Elite_mens_195204_03_sv01" alt="">
                </div>
                <div class="img_sect">
                    <img src="https://res.cloudinary.com/hdsdev/image/upload/c_fill,f_auto,g_center,h_800,q_60,w_800/v1/shoe_finder/products/195337_01_sv01" alt="">
                </div>
           </div>
           <div class="feature_wrap_mode">
                 <img src="../assets/left.svg" alt="">
                 <img src="../assets/left.svg" alt="">
           </div>
    </div>
</template>

<script>
</script>

<style lang="scss">
 .feature_wrap{
    position: relative;
    &_txt{
        position:absolute;
        left: 10%;
        top: 30%;
        width: 20%;
        @include flex_col(.8rem);
        h2{
            font-size: toRem(35);
            color: $blacktxt;
        }
        p{
            font-size: toRem(19);
            line-height: 1.5rem;
        }
        .btn{
            margin-top: 1.5rem;
            @include flex_col(1rem);
            button{
                display: block;
                text-transform: capitalize;
                padding: 1.1rem 1.5rem;
                font-size: 1em;
                background: #ae946d ;
                color: white;
            }
        }
    }
    &_imgScroller{
      display: flex;
      overflow-x: auto;
      flex-wrap:nowrap;
      gap: 0 5rem;
      scroll-snap-type: x mandatory;
      -webkit-overflow-scrolling: touch;
      .img_sect{
          width: 90rem;
          flex-shrink: 0;
           display: flex;
           align-items: center;
           justify-content:flex-end;
          img{
            width: 60%;
          }
      }
    }
    &_mode{
        width: 100%;
        position: absolute;
        @include flex(center,center,4rem);
        top: 80%;
        img{
            cursor: pointer;
            &:nth-child(2){
                transform: rotateY(180deg);
            }
        }

    }
 }
</style>