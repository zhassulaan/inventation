<template>
  <main v-if="show">
    <img src="@/assets/images/background.jpeg" alt="Background" class="background" />
    <Player />
    <section-home />
    <Section>
      <section-about />
    </Section>
    <Border />
    <Section>
      <section-time />
    </Section>
    <Album />
    <Section>
      <section-location />
    </Section>
    <Section>
      <section-host />
    </Section>
    <img src="@/assets/images/bukety.jpg" alt="Wedding flower" />
    <Section>
      <section-countdown />
    </Section>
    <Section>
      <section-form />
    </Section>
  </main>
</template>

<script setup>
const show = ref(false);

const onLoad = () => {
  show.value = true;
};

onMounted(() => {
  window.addEventListener('load', onLoad);
});
onUnmounted(() => {
  window.removeEventListener('load', onLoad);
});
</script>
