<template>
  <div class="time">
    <div>
      <h2>Той салтанаты:</h2>
      <h5>27 шілде 2024</h5>
      <h5 class="time-date">19:00</h5>
    </div>
    <Calendar />
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.time {
  @include container_inner;
  &-image {
    width: 64px;
    height: 64px;
  }
  &-date {
    position: relative;
    width: fit-content;
    margin: 0 auto;
    &::before,
    &::after {
      @include line;
      width: 64px;
    }
    &::before {
      left: -150%;
    }
    &::after {
      right: -150%;
    }
  }
}
</style>
