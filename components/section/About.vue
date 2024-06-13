<template>
  <div class="about">
    <Motion is="h5" preset="popVisible" :duration="750">Құрметті ағайын-туыс, бауырлар, құда-жекжат, нағашы-жиен, бөлелер, дос-жарандар мен әріптестер!</Motion>
    <Motion is="p" preset="popVisible" :duration="750">Сіз(дер)ді балаларымыз</Motion>
    <div>
      <Motion is="h3" preset="slideVisibleLeft" :duration="750">Жасұлан</Motion>
      <Motion is="p" preset="popVisible" :duration="750" class="about-text">мен</Motion>
      <Motion is="h3" preset="slideVisibleRight" :duration="750">Дильназдың</Motion>
    </div>
    <Motion is="p" preset="popVisible" :duration="750">үйлену тойына арналған салтанатты ақ дастарханымыздың қадірлі қонағы болуға шақырамыз!</Motion>
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
