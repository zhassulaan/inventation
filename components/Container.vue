<template>
  <section class="item">
    <slot></slot>
  </section>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.item {
  @include center_block;
  width: 100vw;
  height: 100vh;
  padding: 0 32px;
}
</style>
