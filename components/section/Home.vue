<template>
  <div class="home">
    <div class="home-title">
      <h1 id="zh">Ж</h1>
      <h1 id="and">&</h1>
      <h1 id="d">Д</h1>
    </div>
    <h4 class="home-subtitle">27.07.2024</h4>

    <div class="home-image">
      <img src="@/assets/images/IMG_0655.jpeg" alt="Main image" />
    </div>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.home {
  @include fullpage;
  max-width: 768px;
  &-title,
  &-subtitle {
    @include center;
    z-index: 2;
  }
  &-title {
    width: 320px;
    #zh {
      text-align: left;
    }
    #and {
      text-align: center;
    }
    #d {
      text-align: right;
    }
  }
  &-subtitle {
    top: 90%;
  }
  &-image {
    @include center;
    @include fullpage;
    max-width: 768px;
    &::before,
    &::after {
      @include center;
    }
    &::before {
      @include background;
    }
    &::after {
      content: "";
      width: calc(100% - 28px);
      height: calc(100% - 28px);
      border: 1.5px solid var(--clr-border);
      border-radius: 12px;
    }
  }
}
</style>
