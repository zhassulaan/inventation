<template>
  <div class="map">
    <iframe
      src="https://yandex.com/map-widget/v1/?um=constructor%3Aca50b3c85b2ed186bd1c553263db892ef7da3549df1fd10941c354ee1af004f0&amp;source=constructor"
      width="100%"
      height="100%"
      frameborder="0"
      title="Yandex Map"
    ></iframe>
  </div>
</template>

<style scoped>
.map {
	width: calc(100% - 4px);
	height: 25vh;
	border: 2px solid var(--clr-border);
  border-radius: 16px;
  overflow: hidden;
}
</style>
