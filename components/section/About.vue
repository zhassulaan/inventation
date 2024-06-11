<template>
  <div class="about">
    <h3>Құрметті ағайын-туыс, бауырлар, құда-жекжат, нағашы-жиен, бөлелер, дос-жарандар мен әріптестер!</h3>
    <p class="about-text">Сіз(дер)ді балаларымыз</p>
    <div>
      <h3>Жасұлан</h3>
      <h6>мен</h6>
      <h3>Дильназдың</h3>
    </div>
    <p class="about-text">үйлену тойына арналған салтанатты ақ дастарханымыздың қадірлі қонағы болуға шақырамыз!</p>
    <Album />
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.about {
  position: relative;
  @include container_inner;
}
</style>
