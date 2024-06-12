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
import { VueFlux, FluxPreloader, FluxControls, Img, Fade, Kenburn } from "vue-flux";
import image1 from "@/assets/images/IMG_0688.jpeg";
import image2 from "@/assets/images/IMG_0689.jpeg";
import image3 from "@/assets/images/IMG_0690.jpeg";
import image4 from "@/assets/images/IMG_0691.jpeg";

const options = reactive({
	allowFullscreen: false,
	allowToSkipTransition: false,
	autohideTime: 2000,
	autoplay: true,
	bindKeys: false,
	delay: 2000,
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
  @include fullpage;
  @include border_rad;
  .flux-transition {
    position: absolute;
  }
  & > .flux-image,
  .complements {
    @include origin;
  }
  .complements {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    z-index: 45;
    .remainder {
      flex-basis: 50%;
    }
  }
  .flux-controls {
    @include fullpage;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px;
    .flux-button {
      padding: 0;
      width: 6%;
      min-width: 36px;
      min-height: 36px;
      max-width: 48px;
      max-height: 48px;
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
          stroke: var(--clr-white);
          stroke-width: 14;
          fill: none;
        }
        rect, polygon {
          fill: var(--clr-white);
          stroke-width: 0;
        }
      }
    }
  }
}
</style>
