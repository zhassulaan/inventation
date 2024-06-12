<template>
  <div class="location">
    <h2>Мекен - жайымыз:</h2>
    <h6 class="location-title"><span>"Той сарайы"</span> мейрамханасы, Атырау қ.</h6>
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
