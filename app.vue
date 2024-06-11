<template>
  <vue-scroll-snap :fullscreen="true">
    <img src="@/assets/images/background.jpeg" alt="background" class="background" />
    <img src="@/assets/images/bg_flowers.png" alt="background" class="background" />
    <Player />
    <Section>
      <section-home />
    </Section>
    <Section>
      <section-about />
    </Section>
    <Section>
      <section-time />
    </Section>
    <Section>
      <section-location />
    </Section>
    <Section>
      <section-form />
    </Section>
  </vue-scroll-snap>
</template>

<script setup>
import VueScrollSnap from "vue-scroll-snap";
</script>
