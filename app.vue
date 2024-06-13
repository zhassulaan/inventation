<template>
  <main>
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
      <Motion is="p" preset="fadeVisible" :duration="750">
        <Album />
      </Motion>
      <Section>
        <section-location />
      </Section>
      <Section>
        <section-host />
      </Section>
      <Motion is="p" preset="fadeVisible" :duration="750">
        <img src="@/assets/images/bukety.jpg" alt="Wedding flower" />
      </Motion>
      <Section>
        <section-countdown />
      </Section>
      <Section>
        <section-form />
      </Section>
  </main>
</template>
