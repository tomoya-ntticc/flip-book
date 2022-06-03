<script setup lang="ts">
import { ref, reactive } from 'vue'
import SwiperClass from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
import SwiperCore, { EffectFlip, Autoplay } from 'swiper';
import 'swiper/css';
import "swiper/css/effect-flip";
import '../style.css';

import nature_1 from '../assets/nature-1.jpg'
import nature_2 from '../assets/nature-2.jpg'


SwiperCore.use([EffectFlip, Autoplay]);

const swiperRef = ref();

const onSwiper = (swiper: SwiperClass) => {
  console.log(swiper);
  swiperRef.value = swiper;
};

const store = reactive({
  files: [nature_1, nature_2]
})
</script>

<template>
  <swiper
    :effect="'flip'"
    :grabCursor="true"
    :centeredSlides="true"
    :slidesPerView="'auto'"
    :speed="1000"
    :autoplay="{
      delay: 2500,
      disableOnInteraction: false,
    }"
    @swiper="onSwiper"
  >
    <swiper-slide v-for="(file, index) in store.files" :key="index">
      <img :src="file" />
    </swiper-slide>
  </swiper>
</template>