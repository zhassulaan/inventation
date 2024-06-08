<template>
  <div id="about" class="about">
    <h4>Құрметті қонақтар!</h4>
    <p class="about-text">Сіз(дер)ді балаларымыз</p>
    <div>
      <h3>Жасұлан</h3>
      <h6>мен</h6>
      <h3>Дильназдың</h3>
    </div>
    <p class="about-text">үйлену тойына арналған салтанатты ақ дастарханымыздың қадірлі қонағы болуға шақырамыз!</p>
    <img src="@/assets/images/flowers.png" alt="Flowers" />
    <Album />
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.about {
  position: relative;
  @include container_inner;
  &-text {
    font-size: 18px;
  }
}
</style>
