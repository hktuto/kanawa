<template>
    <div class="menuContainer">
        <Drawer :is-open="isDrawerOpen" background-color="#fff" max-width="90%" :speed="500" @close="closeDrawer">
            <div class="menuHeader">

            <Logo class="menuLogo" />
            <div class="siteTitle">
                嘉麗華集團 <br />
                Kanawa Group
            </div>
            </div>
            <div v-for="item in menuItems" :key="item.label" class="menuItem" @click="itemClick(item)">
                {{ item.label }}
            </div>
        </Drawer>
        <template v-if="smallerThanSm" >
            <div class="mobileIcon">
                <div :class="{'icon-wrapper':true, isDrawerOpen}" @click="toggleDrawer">
                    <label class="hamburger">
                        <input class="hamburger-input" type="checkbox">
                        <span class="hamburger-line first"></span>
                        <span class="hamburger-line second"></span>
                        <span class="hamburger-line third"></span>
                    </label>
                </div>
            </div>
        </template>
        <template v-else >
            <div v-for="item in menuItems" :key="item.label" class="menuItem" @click="itemClick(item)">
                {{ item.label }}
            </div>
        </template>
        
    </div>
</template>


<script lang="ts" setup>
    import { breakpointsTailwind, useBreakpoints } from '@vueuse/core'
    const router = useRouter();
    const breakpoints = useBreakpoints(breakpointsTailwind)
    const smallerThanSm = breakpoints.smaller('sm')
    const menuItems = [
        {
            label:"企業簡介",
            url:"/about",
        },
        {
            label:'企業設備',
            url:"/equipment"
        },
        {
            label:'產品展示',
            url:"/product"
        },
        {
            label:'企業責任',
            url:"/responsibility"
        },
        {
            label:'聯絡我們',
            url:"/contact"
        },
    ]
        const isDrawerOpen = ref(false);
        function toggleDrawer() {
            isDrawerOpen.value = !isDrawerOpen.value;
        }

        function closeDrawer() {
            isDrawerOpen.value = false;
        }
    function itemClick(item:any){
        window.location = item.url;
    }
</script>

<style lang="scss" scoped>

    .menuHeader{
        display: flex;
        flex-flow: row nowrap;
        justify-content: flex-start;
        align-items: center;
    }
    .siteTitle{
        margin-left: 12px;
    }
    .mobileIcon{
        position: fixed;
        top: 10px;
        right: 24px;
        z-index: 9999;
    }
    .menuLogo{
        width: 60px;
    }
    .menuContainer{
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
        align-items: flex-start;
    }

    .menuItem{
        padding: var(--app-space);
        cursor: pointer;
        font-size: 1rem;
    }

    .hamburger {
  position: relative;
  width: 40px;
  height: 40px;
  display: inline-flex;
  flex-direction: column;
  justify-content: space-between;
  cursor: pointer;
  padding: 10px;
  
  &:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 20px;
    background: #ce2525;  /* fallback for old browsers */
    background: -webkit-linear-gradient(to right, #be1010, #870909);  /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to right, #be1010, #870909); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    transform: rotate(0deg);
    transition: all 0.4s cubic-bezier(0.54, -0.10, 0.57, 0.57);
  }
  
  .hamburger-input {
    position: absolute;
    opacity: 0;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    cursor: pointer;
  }
  
  .hamburger-line {
    width: 100%;
    background: #fff;
    height: 2px;
    display: block;
    border-radius: 6px;
    transition: transform 0.4s cubic-bezier(0.54, -0.81, 0.57, 0.57);
    position: relative;
    
    &.first,
    &.third {
      width: 50%;
    }
    
    &.third {
      margin-left: 50%;
      transform-origin: left;
    }
  }
}

.isDrawerOpen{
    .hamburger-line.second {
    transform: rotate(-45deg); 
  }
    .hamburger-line.first {
    transform: translate(2px, 6px) rotate(-135deg);
  }
  .hamburger-line.first {
    transform: translate(2px, 8px) rotate(-135deg);
  }
  .hamburger-line.third {
    transform: translate(9px, -1px) rotate(-135deg);
  }
  .hamburger:before {
    transform: rotate(45deg);
  }
}
</style>