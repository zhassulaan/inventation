<template>
  <div id="about" class="about">
    <p class="about-text">Құрметті қонақтар!</p>
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
.about {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 32px;
}
</style>
