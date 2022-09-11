<template>
    <NuxtLayout name="content">
        <h1>企業設備 </h1>
        <div class="slideContainer">
          <vue-easy-lightbox :visible="visibleRef" :imgs="slides" :index="indexRef" @hide="onHide"></vue-easy-lightbox>
        <Swiper
                :modules="modules"
                :slides-per-view="3"
                :space-between="4"
                :loop="true"
                :autoplay="autoplay"
            >
                <SwiperSlide v-for="(slide, i) in slides" :key="slide" class="slide">
                  <div class="imgContainer" @click="showImg(i)">
                    <img :src="slide" />
                  </div>
                </SwiperSlide>
            </Swiper>
        </div>
        <h2>
          辦公室
        </h2>
        <p>
本集團辦公空間寬敞明亮，內設中央空調，擺放綠色盆景，空氣清新，環境怡人，為員工提供優美舒適精神飽滿的工作環境。
        </p>
        <h2>
          廠房
        </h2>
        <p>
        本集團在中國香港及中國內地設有多個自營和聯營大型生產基地，擁有數千名員工之生產力，月產量高達600,000件; 豐富的經驗，完善的管理，再加上先進的設備，必定能滿足客戶的需求。我們有近千台世界先進的日本司馬 、德國士都及國產慈星電腦針織橫機以協助生產，機種靈活，速度快，任何設計都能應付自如。
        </p>
        <h3>
產品開發與設計
        </h3>
        <p>
我們亦非常關注針織時裝之潮流。我們在香港和國內均設有開發設計部，擁有時尚的樣板展廳和專業的設計師團隊，緊貼國際時尚步伐。除了客戶提供之款式外，本集團每年自行設計之款式超過1500款，以供客戶選擇各種不同之設計風格及針法。
集團目前擁有一支跨國組合的設計師隊伍，他們出身時尚的國度，有卓越的藝術修養和獨到設計見解, 在紐約、米蘭、東京等時尚名城都留下過他們輝煌的印跡。採用先進的管理方式，時尚的設計理念，加上數字化的設備，保障品牌在款式設計、質量和價格上都有很大的競爭力。
        </p>

  </NuxtLayout>
</template>

<script lang="ts" setup>
  import VueEasyLightbox from 'vue-easy-lightbox'
  import 'vue-easy-lightbox/external-css/vue-easy-lightbox.css'
    import { Swiper, SwiperSlide } from 'swiper/vue';
    import { Autoplay } from 'swiper'
    import 'swiper/css'
    import 'swiper/css/pagination'
    import 'swiper/css/navigation'
    const modules = [ Autoplay];
  
    const slides = [
      'images/07.JPG',
      'images/08.JPG',
      'images/09.JPG',
      'images/10.JPG',
      'images/11.JPG',
      'images/12.JPG'
    ]
    const autoplay = {
        delay: 2000
    }

    const visibleRef = ref(false);
  const indexRef = ref(0);

  const onHide = () => visibleRef.value = false
  const showImg = (index:number) => {
    visibleRef.value = true;
    indexRef.value = index;
  }
</script>

<style lang="scss" setup>
  .imgContainer{
    aspect-ratio: 4/3;
    overflow: hidden;
    position: relative;
    cursor: pointer;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  .slideContainer{
    width: 100%;
    // height: 250px;
    position: relative;
  }
</style>