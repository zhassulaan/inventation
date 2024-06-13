<template>
  <div class="host">
    <MotionGroup preset="slideVisibleBottom" :duration="750">
      <h2>Той иелері:</h2>
      <h5>Серік - Ляззат</h5>
    </MotionGroup>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.host {
  @include container_inner;
}
</style>
