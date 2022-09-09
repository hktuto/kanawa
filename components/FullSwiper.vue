<template>
    <div class="swiperContainer">
        <Swiper
                :modules="modules"
                :loop="true"
                :autoplay="autoplay"
            >
                <SwiperSlide v-for="slide in slides" :key="slide" class="slide">
                    <div class="imgContainer">
                        <img :src="(!smallerThanSm ? slide  : slide + '-mobile' ) + '.jpg'" />
                    </div>
                </SwiperSlide>
            </Swiper>
    </div>
</template>

<script lang="ts" setup>
    import { Swiper, SwiperSlide } from 'swiper/vue';
    import { Pagination, Navigation, Autoplay } from 'swiper'
    import { breakpointsTailwind, useBreakpoints } from '@vueuse/core'
    import 'swiper/css'
    import 'swiper/css/pagination'
    import 'swiper/css/navigation'
    const modules = [Pagination, Autoplay]
    const breakpoints = useBreakpoints(breakpointsTailwind)
    const smallerThanSm = breakpoints.smaller('sm')
    const slides = [
        "/images/slide1",
        "/images/slide2",
        "/images/slide3",
        "/images/slide4",
        "/images/slide5",
        "/images/slide6",
    ]

    const autoplay = {
        delay: 5000
    }
</script>

<style lang="scss" scoped>
.imgContainer{
    width:100%;
    height: 100%;
    img{
        width:100%;
        height: 100%;
        object-fit: contain;
    }
}
</style>