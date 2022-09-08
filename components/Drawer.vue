
  <script lang="ts" setup>
    import { onClickOutside } from '@vueuse/core'

    const drawerContent = ref(null);
    const props = defineProps<
        {
            isOpen: boolean,
            speed: number,
            maxWidth: String,
            backgroundColor: String
        }
    >();
    const { isOpen } = toRefs(props)
    const isTransitioning = ref(false);
    const isVisible = ref(false)
    const emit = defineEmits(['close'])
    onClickOutside(drawerContent, (event) => closeDrawer())
    
    function toggleBackgroundScrolling(enable) {
      const body = document.querySelector("body");
      body.style.overflow = enable ? "hidden" : null;
    }

    function closeDrawer() {
      if (!isTransitioning.value) {
        emit("close");
      }
    }


    onMounted(() =>{
        isVisible.value = props.isOpen;
    })

    watch( isOpen, (val) =>{
        isTransitioning.value = true;

        if (val) {
            toggleBackgroundScrolling(true);
            isVisible.value = true;
        } else {
            toggleBackgroundScrolling(false);
            setTimeout(() => (isVisible.value = false), props.speed);
        }

        setTimeout(() => (isTransitioning.value = false), props.speed);
        } )
  </script>

<template>
    <div>
      <div  class="drawer" :class="{ 'is-open': isOpen, 'is-visible': isVisible }">
        <div
          class="drawer__overlay"
          :style="{ transitionDuration: `${speed}ms` }"
        ></div>
        <div
            ref="drawerContent"
          class="drawer__content"
          :style="{
            maxWidth,
            transitionDuration: `${speed}ms`,
            backgroundColor: backgroundColor,
          }"
        >
          <slot></slot>
        </div>
      </div>
    </div>
  </template>


<style lang="scss" scoped>
.drawer {
  visibility: hidden;

  &.is-visible {
    visibility: visible;
  }

  &.is-open {
    .drawer__overlay {
      opacity: 0.5;
    }

    .drawer__content {
      transform: translateX(0);
      padding: 1rem;
      border-top-left-radius: 12px;
      border-bottom-left-radius: 12px;
    }
  }

  &__overlay {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    z-index: 200;
    opacity: 0;
    transition-property: opacity;
    background-color: #000000;
    user-select: none;
  }

  &__content {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    height: 100%;
    width: 100%;
    z-index: 9999;
    overflow: auto;
    transition-property: transform;
    display: flex;
    flex-direction: column;
    transform: translateX(100%);
    box-shadow: 0 2px 6px #777;
  }
}
</style>
