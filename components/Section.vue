<template>
  <section class="item">
    <slot></slot>
  </section>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.item {
  padding: 56px 32px;
}
</style>
