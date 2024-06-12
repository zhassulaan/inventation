<template>
  <div class="time">
    <h2>Той салтанаты:</h2>
    <div>
      <h6 class="time-date">27 шілде 2024</h6>
      <h6 class="time-date">19:00</h6>
    </div>
    <Calendar />
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.time {
  @include container_inner;
  &-date {
    &:first-child {
      text-transform: uppercase;
    }
    &:last-child {
      position: relative;
      width: fit-content;
      margin: 8px auto 0;
      &::before,
      &::after {
        @include line;
        width: 64px;
        height: 1.5px;
      }
      &::before {
        left: -175%;
      }
      &::after {
        right: -175%;
      }
    }
  }
}
</style>
