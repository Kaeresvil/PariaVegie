<template>
  <ion-page>
    <ion-content :fullscreen="true">
       <swiper class="slidePage"
    :modules="modules"
    :autoplay="{
      delay: 2000,
    }"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
  <!-- slide for first page -->
        <swiper-slide>
    <Splash/> 
        </swiper-slide>


    <!-- slide for HomePage -->
        <swiper-slide>
  <HomePage/>
        </swiper-slide>
       
      </swiper>
    </ion-content>
  </ion-page>
</template>


<script>
import { defineComponent } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import {  Autoplay, A11y } from 'swiper';
import { IonContent, IonPage } from '@ionic/vue';
import Splash from './Splash.vue'
import HomePage from './HomePage.vue'

import 'swiper/css';
import 'swiper/css/autoplay';
import '@ionic/vue/css/ionic-swiper.css';
export default defineComponent({
     name: 'SliderPage',
  
  components: { 
    Swiper,
    SwiperSlide,
    IonContent,
    IonPage, 
    Splash,  
    HomePage,  
},
    setup() {
      
      const onSlideChange = (swiper) => {
        swiper.autoplay.running = false;

         if (swiper.activeIndex == 1){
        swiper.allowSlideNext = false;
        swiper.allowSlidePrev = true;
  
      }else if(swiper.activeIndex == 0){
         swiper.allowSlideNext = true;
         swiper.allowSlidePrev = false;
      }
      };
      return {
        onSlideChange,
         modules: [ Autoplay, A11y]
      };
    },
});
</script>
<style scoped>
.slidePage{
    height: 100%;
}
</style>