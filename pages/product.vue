<template>
    <NuxtLayout name="content">
        <div class="sectionHeader">
          <h1>產品展示</h1>
        </div>
        <vue-easy-lightbox :visible="visibleRef" :imgs="images" :index="indexRef" @hide="onHide"></vue-easy-lightbox>
        <div class="imageGrid">
          <div v-for="(item,index) in images" :key="item" class="gridItem" @click="showImg(index)">
            <img :src="item" />
          </div>
        </div>
  </NuxtLayout>
</template>

<script lang="ts" setup>
  import VueEasyLightbox from 'vue-easy-lightbox'
  import 'vue-easy-lightbox/external-css/vue-easy-lightbox.css'
  const images = [
    '/images/products/001Ana R.JPG',
    '/images/products/002RainLi.JPG',
    '/images/products/003RainLi.JPG',
    '/images/products/004朱晨丽.JPG',
    '/images/products/005RainkyWai.JPG',
    '/images/products/ZD__3437.JPG',
    '/images/products/ZD__3489.JPG',
    '/images/products/ZD__3595.JPG',
    '/images/products/ZD__3798.JPG',
    '/images/products/ZD__3937.JPG',
    '/images/products/ZD__4151.JPG',
    '/images/products/ZD__4590.JPG',
    '/images/products/ZD__4646.JPG'
  ]

  const visibleRef = ref(false);
  const indexRef = ref(0);

  const onHide = () => visibleRef.value = false
  const showImg = (index:number) => {
    visibleRef.value = true;
    indexRef.value = index;
  }
</script>


<style lang="scss" scoped>
.imageGrid{
  width:100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 8px;
  .gridItem{
    aspect-ratio: 1/1;
    cursor: pointer;
    img{
      width: 100%;
      height: 100%;
      object-fit: contain;
    }
  }
}
</style>