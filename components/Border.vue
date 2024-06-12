<template>
  <div class="border">
    <font-awesome-icon icon="heart" class="border-icon" />
  </div>
</template>

<script setup>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { library } from "@fortawesome/fontawesome-svg-core";
import { faHeart } from "@fortawesome/free-solid-svg-icons";

library.add(faHeart);
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.border {
  position: relative;
  @include center_block;
	&-icon {
    position: relative;
    width: 16px;
    height: 16px;
    color: var(--clr-gold);
  }
  &::before,
  &::after {
    @include line;
    width: calc(50% - 72px);
    height: .5px;
  }
  &::before {
    left: 32px;
  }
  &::after {
    right: 32px;
  }
}
</style>
