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

onMounted(() => {
  if (document.readyState === 'complete') {
    show.value = true;
  } else {
    document.querySelector("body").style.visibility = "hidden";
    document.onreadystatechange = function() {
      if (document.readyState === "complete") {
        document.querySelector("body").style.visibility = "visible";
        show.value = true;
      }
    }
  }
});
</script>
