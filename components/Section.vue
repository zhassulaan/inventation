<template>
  <section class="item">
    <slot></slot>
  </section>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.item {
  padding: 64px 32px;
}
</style>
