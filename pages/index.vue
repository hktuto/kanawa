<template>
    <div class="content">
        <Header />
        <FullSwiper />
        <Footer />
    </div>
</template>

<script lang="ts" setup>
    
</script>

<style lang="scss" scoped>
    .content{
        width: 100vw;
        height: 100%;
        overflow: hidden;
        position: relative;
        display: grid;
        grid-auto-columns: 1fr;
        grid-template-rows: min-content 1fr;
    }
    .swiperContainer{
        width: 100vw;
        // aspect-ratio: 16 / 9;
        @media (max-width: 640px){
            // aspect-ratio: 8 / 16;
        }
    }
    .headerContainer{
        width:100%;
    }
    .footerContainer{
        position: fixed;
        left:0;
        bottom:0;
        width:100%;
        z-index: 9;
    }
</style>