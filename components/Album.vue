<template>
  <Swiper
    :modules="[Autoplay, Navigation, EffectFade]"
    :spaceBetween="30"
    :autoplay="autoplay"
    :navigation="true"
    :loop="true"
    effect="fade"
  >
    <SwiperSlide v-for="(image, index) in images" :key="index">
      <img :src="image" :alt="`Slide ${index + 1}`" />
    </SwiperSlide>
  </Swiper>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Navigation, EffectFade } from "swiper";
import image1 from "@/assets/images/IMG_0688.jpeg";
import image2 from "@/assets/images/IMG_0689.jpeg";
import image3 from "@/assets/images/IMG_0690.jpeg";
import image4 from "@/assets/images/IMG_0691.jpeg";
import "swiper/css";
import "swiper/css/autoplay";
import "swiper/css/navigation";
import "swiper/css/effect-fade";

const images = ref([image1, image2, image3, image4]);
const autoplay = {
  delay: 3500,
  disableOnInteraction: false,
};
</script>

<style lang="scss">
@use "@/assets/styles/mixins" as *;

.swiper {
  @include fullpage;
  @include border_rad;
  &-slide {
    visibility: hidden;
    &-active {
      visibility: visible;
    }
  }
}
</style>
