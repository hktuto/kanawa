<template>
    <NuxtLayout name="content">
        <h1>企業簡介 </h1>
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
        <p>嘉麗華集團於1988年在中國香港成立，為香港著名毛衣生產商。本集團致力為全球多家服裝品牌及零售商進行毛衣設計及生產。經過多年的持續發展，在毛織業界響負盛名。本集團在香港及中國內地有多個生產基地，擁有數千名員工之生產力，並有近千台全球最先進之日本司馬、德國士都與國產慈星電腦針織橫機以協助生產。為了積極拓展中國內銷市場，本集團於2006年成立中國境內辦事處，為廣大客戶提供專業、快捷和完善之毛衣貼牌加工服務。集團亦積極拓展零售市場，包括於2011年創立香港本地時裝品牌”EQUALITY”及收購澳洲知名連鎖女裝品牌”Brown Sugar Australia”，為開發全球零售市場打下堅實的基礎。
此外，集團亦積極參與世界各地之金融、房地產、租賃、及貿易等投資項目，令業務更多元化。
</p>
  <h2>主要客戶 Major customers
</h2>
<p>Axcess, Liz & Co, Concepts, Axcess Mens, Claiborne Mens
Canyon River Blues, Covington, Covington Sport, Structure, 
Intimates, Apostrophe,Jaclyn Smiths, Basic Editions, Attention, 
Route 66, Argyle Culture, Cavi, Marc Ecko, Rocawear, Emma James, 
Chico’s, Urban Outifitters, Rebecca Moses, Delia’s, Forever 21, 
QVC-HSN, KVZ, JH Collectibles, D.K.N.Y., Anthropologie, Oliver Juice
Tribal, Cleo, Pimkie, Dusen, Urban Outfitters UK, Evisu, 歌莉婭、安奈兒、E&You、沐蘭、波頓、優美世界、紛麗、紐方、風韻雅、
奧菲、尹美爾、浪比時、小虎憨尼、小熊B琪、歌妮思、麗尚、Moveup、
美孩兒、瑪克西妮、諾瑪茜、沙娃、沙丘、約瑟芬，嘉淇洛、傑萊、海弘、
露裡娃、澳絲蓮、菲妮迪、賽爾美、加利高、183SX、螞蟻仔
</p>
<h2>品牌介绍:</h2>
<p>
EQUALITY, 集團於2011年創立的香港本地時裝品牌。品牌風格以歐美設計為主，簡約大方。設計師以最新潮流訊息，時尚的創意、配合新穎的面料，為都市女性打造時尚優雅的服裝。品牌自推出以來。深受城中名人喜愛,包括: 香港名模Ana R., 著名影星李彩華，香港小姐冠軍朱晨麗及歌手蔚雨芯等。品牌亦成為電影《喜愛夜蒲3》及舞台劇《Upcycle me》的官方指定服裝之一。
此外，EQUALITY更獲香港貿發局選為「2013香港時尚購物展•青島」&lt;名品匯>品牌，與謝瑞麟珠寶,金至尊珠寶,佐丹奴等一同作為重點推廣的香港品牌。
</p>

<h1>About us:</h1>
<p>Kanawa Group, a sweater manufacturer and exporter in Hong Kong SAR and China since 1988. Our products are mainly sold to the United States, Canada, Europe and China. We focus on making men’s, ladies' and kids' knitwear from 3 to 14 gauges, with construction of intarsia, floating jacquard, tubular jacquard and even hand-knit and hand-crochet. 

Apart from our headquarters in Hong Kong SAR and our representative office in Shenzhen, China, we also operate and co-operate with factories in Hong Kong SAR and China with almost a thousand automatic computerized knitting machines. Our manufacturing capacity is around 50,000 dozens per month.

The mission of our Group is to provide innovative design and high quality products with value pricing, while establishing a successful relationship with our customers and suppliers. Therefore, we are not only having a professional designing team and a strong manufacturing team, but also maintaining close connections with yarn mills from China and Taiwan. As better offers are provided by these suppliers, our customers can be benefited directly, in order to cope with keen competitions in the market. 

In addition, we have acquired a well-known clothing brand from overseas, "Brown Sugar Australia", and also started up our own clothing brand, "EQUALITY” since 2011.
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
      '/images/01.JPG',
      '/images/02.JPG',
      '/images/03.JPG',
      '/images/04.JPG',
      '/images/05.JPG',
      '/images/06.JPG'
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