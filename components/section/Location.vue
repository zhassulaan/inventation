<template>
  <div class="location">
    <h2>Мекен - жайымыз:</h2>
    <div>
      <h6><span>"Той сарайы"</span> мейрамханасы,</h6>
      <h6>Атырау қ.</h6>
    </div>
    <a href="https://go.2gis.com/h727u">
      <img src="@/assets/images/2gis.png" alt="2Gis" class="location-icon" />
    </a>
    <a href="https://go.2gis.com/h727u">
      <Map />
    </a>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.location {
  @include container_inner;
  align-items: center;
  span {
    text-decoration: underline;
  }
  &-icon {
    width: 64px;
    height: 64px;
    margin: 0 auto;
  }
}
</style>
