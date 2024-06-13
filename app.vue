<template>
  <main>
    <img src="@/assets/images/background.jpeg" alt="Background" class="background" />
    <MotionGroup preset="popVisible" :duration="300">
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
    </MotionGroup>
  </main>
</template>
