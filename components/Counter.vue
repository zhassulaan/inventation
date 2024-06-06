<template>
  <div class="counter">
    <img :src="image" alt="Counter image" />
    <div class="counter-countdown">
      <h3 class="counter-countdown__time">{{ time }}</h3>
      <p class="counter-countdown__label">{{ label }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  time: Number,
  label: String,
  image: String
});
</script>

<style scoped lang="scss">
@use "@/assets/styles/vars" as *;
@use "@/assets/styles/mixins" as *;

.counter {
  position: relative;
  width: 22%;
  border-radius: 16px;
  overflow: hidden;
  &::after {
    @include origin;
    @include background;
  }
  &-countdown {
    position: absolute;
    bottom: 0;
    @include center;
    z-index: 2;
    &__time,
    &__label {
      text-align: center;
      color: var(--clr-white);
    }
  }
}
</style>
