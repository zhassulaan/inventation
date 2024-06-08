<template>
  <VueFlux
   :options="options"
   :rscs="rscs"
   :transitions="transitions"
  >
   <template #preloader="preloaderProps">
      <FluxPreloader v-bind="preloaderProps" />
   </template>

   <template #controls="controlsProps">
      <FluxControls v-bind="controlsProps" />
   </template>
</VueFlux>
</template>

<script setup>
import { VueFlux, FluxPreloader, FluxControls, Img, Fade, Kenburn } from 'vue-flux';
import image1 from '@/assets/images/IMG_0688.jpeg';
import image2 from '@/assets/images/IMG_0689.jpeg';
import image3 from '@/assets/images/IMG_0690.jpeg';
import image4 from '@/assets/images/IMG_0691.jpeg';

const options = reactive({
	allowFullscreen: false,
	allowToSkipTransition: true,
	autohideTime: 2500,
	autoplay: false,
	bindKeys: false,
	delay: 5000,
	enableGestures: false,
	infinite: true,
	lazyLoad: true,
	lazyLoadAfter: 3,
});
const rscs = shallowReactive([
	new Img(image1),
	new Img(image2),
	new Img(image3),
	new Img(image4)
]);
const transitions = shallowReactive([
  Fade,
  Kenburn,
]);
</script>

<style lang="scss">
@use "@/assets/styles/mixins" as *;

.vue-flux {
  position: relative;
  width: 220px;
  height: 280px;
  @include border_rad;
  .flux-transition {
    position: absolute;
  }
  & > .flux-image {
    position: absolute;
    top: 0;
    left: 0;
  }
  .complements {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    z-index: 45;
    .remainder {
      flex-basis: 50%;
    }
  }
  .flux-controls {
    display: flex;
    justify-content: space-between;
    padding: 16px;
    .flux-button {
      padding: 0;
      width: 6%;
      min-width: 24px;
      min-height: 24px;
      max-width: 36px;
      max-height: 36px;
    }
  }
}

.flux-button {
  border: 0;
  cursor: pointer;
  background-color: transparent;
  &:hover {
    > svg {
      line, polyline {
        stroke: yellow;
      }
      rect, polygon {
        fill: yellow;
      }
    }
  }
  > svg {
    width: 100%;
    > circle {
      fill: rgba(0, 0, 0, 0.7);
    }
    line, polyline, rect, polygon {
      stroke-linecap: round;
      stroke-linejoin: round;
      stroke: white;
      stroke-width: 14;
      fill: none;
    }
    rect, polygon {
      fill: white;
      stroke-width: 0;
    }
  }
}
</style>
