<template>
  <div class="about">
    <h5>Құрметті ағайын-туыс, бауырлар, құда-жекжат, нағашы-жиен, бөлелер, дос-жарандар мен әріптестер!</h5>
    <p>Сіз(дер)ді балаларымыз</p>
    <div>
      <h3>Жасұлан</h3>
      <p class="about-text">мен</p>
      <h3>Дильназдың</h3>
    </div>
    <p>үйлену тойына арналған салтанатты ақ дастарханымыздың қадірлі қонағы болуға шақырамыз!</p>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.about {
  @include container_inner;
  &-text {
    margin: 6px 0 4px;
  }
}
</style>
