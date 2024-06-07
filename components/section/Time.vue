<template>
  <div id="time" class="time">
    <Countdown />
    <div>
      <h4>Той салтанаты:</h4>
      <h3>27 шілде 2024</h3>
    </div>
    <Calendar />
    <div>
      <h4>Басталу уақыты:</h4>
      <h3 class="time-date">19:00</h3>
    </div>
  </div>
</template>

<style scoped lang="scss">
.time {
  display: flex;
  flex-direction: column;
  gap: 40px;
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
      position: absolute;
      content: '';
      top: 50%;
      transform: translateY(-50%);
      width: 64px;
      height: 1.5px;
      background-color: var(--clr-primary)
    }
    &::before {
      left: -120%;
    }
    &::after {
      right: -120%;
    }
  }
}
</style>
