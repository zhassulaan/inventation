<template>
  <div class="counter">
    <img :src="image" alt="Counter image" />
    <div class="counter-countdown">
      <p class="counter-countdown__time">{{ time }}</p>
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
@use "@/assets/styles/mixins" as *;

.counter {
  position: relative;
  width: 23%;
  height: 160px;
  border-radius: 16px;
  overflow: hidden;
  &::after {
    @include origin;
    @include background;
    background-color: var(--clr-black);
  }
  &-countdown {
    @include center;
    @include col;
    z-index: 2;
    &__time,
    &__label {
      text-align: center;
      color: var(--clr-white);
    }
    &__time {
      font-size: 28px;
    }
    &__label {
      font-size: 16px;
    }
  }
}
</style>
