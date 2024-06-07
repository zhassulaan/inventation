<template>
  <section class="container">
    <slot></slot>
  </section>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.container {
  @include center_block;
  width: 100vw;
  height: 100vh;
  scroll-snap-align: start;
  padding: 0 32px;
}
</style>
