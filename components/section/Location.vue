<template>
  <div id="location" class="location">
    <h4>Мекен жайымыз:</h4>
    <h5 class="location-title"><span>"Той сарайы"</span> мейрамханасы, Атырау қ.</h5>
    <a href="https://go.2gis.com/h727u">
      <img src="@/assets/images/2gis.png" alt="Map" class="location-icon" />
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
  &-title span {
    text-decoration: underline;
  }
  &-icon {
    width: 64px;
    height: 64px;
    margin: 0 auto;
  }
}
</style>
