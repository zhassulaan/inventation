<template>
  <vue-scroll-snap :fullscreen="true">
    <img src="@/assets/images/background.jpeg" alt="background" class="main-background" />
    <img src="@/assets/images/bg_flowers.png" alt="background" class="main-background" />
    <Container>
      <section-home />
    </Container>
    <Container>
      <section-about />
    </Container>
    <Container>
      <section-time />
    </Container>
    <Container>
      <section-location />
    </Container>
    <Container>
      <section-form />
    </Container>
  </vue-scroll-snap>
</template>

<script setup>
import VueScrollSnap from "vue-scroll-snap";
</script>
