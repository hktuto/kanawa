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
        height: 100vh;
        overflow: hidden;
        position: relative;
        display: grid;
        grid-auto-columns: 1fr;
        grid-template-rows: min-content 1fr;
    }
    .swiperContainer{
        width: 100vw;
    }
    .headerContainer{
        width:100%;
    }
    .footerContainer{
        position: absolute;
        left:0;
        bottom:0;
        width:100%;
        z-index: 9;
    }
</style>