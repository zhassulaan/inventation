<template>
  <div class="time">
    <Motion is="h2" preset="fadeVisible" :duration="750">Той салтанаты:</Motion>
    <div>
      <Motion is="h6" class="time-date" preset="fadeVisible" :duration="750">27 шілде 2024</Motion>
      <Motion is="h6" class="time-date" preset="fadeVisible" :duration="750">19:00</Motion>
      </div>
    <MotionGroup preset="fadeVisible" :duration="750">
      <Calendar />
    </MotionGroup>
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
