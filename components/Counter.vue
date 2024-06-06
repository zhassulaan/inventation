<template>
  <div class="counter">
    <img :src="image" alt="Counter image" />
    <div class="counter-countdown">
      <span class="counter-countdown__time">{{ time }}</span>
      <span class="counter-countdown__label">{{ label }}</span>
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
    background-color: var(--clr-black);
  }
  &-countdown {
    position: absolute;
    bottom: 0;
    @include center;
    display: flex;
    flex-direction: column;
    z-index: 2;
    &__time,
    &__label {
      text-align: center;
      color: var(--clr-white);
    }
    &__time {
      font-size: 32px;
    }
    &__label {
      font-size: 20px;
    }
  }
}
</style>
