<script setup lang="ts">
import { ref, reactive } from 'vue'
import SwiperClass from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
import SwiperCore, { EffectFlip, Autoplay } from 'swiper';
import 'swiper/css';
import "swiper/css/effect-flip";
import '../style.css';

import crow_1 from '../assets/crow_1.jpg'
import crow_2 from '../assets/crow_2.jpg'
import beautiful_drawing_1 from '../assets/beautiful_drawing_1.jpg'
import beautiful_drawing_2 from '../assets/beautiful_drawing_2.jpg'


SwiperCore.use([EffectFlip, Autoplay]);

const swiperRef = ref();

const onSwiper = (swiper: SwiperClass) => {
  console.log(swiper);
  swiperRef.value = swiper;
};

const store = reactive({
  files: [beautiful_drawing_1, beautiful_drawing_2]
})
</script>

<template>
  <swiper
    class="w-10/12"
    :effect="'flip'"
    :grabCursor="true"
    :centeredSlides="true"
    :slidesPerView="'auto'"
    :speed="5000"
    :autoplay="{
      delay: 5000,
      disableOnInteraction: false,
    }"
    @swiper="onSwiper"
  >
    <swiper-slide v-for="(file, index) in store.files" :key="index">
      <img :src="file" />
    </swiper-slide>
  </swiper>
</template>