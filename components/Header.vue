<template>
    <div class="headerContainer">
        <div class="iconContent">

            <Logo class="headerLogo" />
            <div class="siteTitle">
                嘉麗華集團 <br />
                Kanawa Group
            </div>
        </div>
        <!--  -->
        <Menu />
    </div>
</template>

<script lang="ts" setup>
    
</script>

<style lang="scss" >
    .iconContent{
        display: flex;
        flex: row nowrap;
        justify-content: flex-start;
        align-items: center;

    }
    .headerContainer{
        padding: var(--app-space) calc( var(--app-space) * 2);
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        background: rgba(255,255,255,0.8);
    }
    .headerLogo{
        width: 60px;
        // margin: 0 auto;
        display: block;
        @media (max-width: 640px) {
            width: 40px;
        }
    }
    .siteTitle{
        margin-left: 12px;
        text-align: left;
        font-size: clamp(0.6rem, -0.875rem + 8.333vw, 1rem);
        font-weight: 700;
        color: #000;
        display: block;
    }
</style>