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
    }
    .headerContainer{
        position: absolute;
        left:0;
        top:0;
        width:100%;
        z-index: 9;
    }
    .footerContainer{
        position: absolute;
        left:0;
        bottom:0;
        width:100%;
        z-index: 9;
    }
</style>