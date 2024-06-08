<template>
  <div id="location" class="location">
    <h4 class="location-title">Мекен жайымыз:</h4>
    <h3 class="location-subtitle">"Той сарайы" мейрамханасы, Атырау қ.</h3>
    <img src="@/assets/images/2gis.png" alt="Map" class="location-icon" />
    <Map />
  </div>
</template>

<style scoped lang="scss">
.location {
  display: flex;
  flex-direction: column;
  gap: 24px;
  &-icon {
    width: 64px;
    height: 64px;
    margin: 0 auto;
  }
}
</style>
