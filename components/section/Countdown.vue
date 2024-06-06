<template>
  <div id="about" class="home-content main">

    <div class="about-content">
      <Counter
        v-if="hydrated"
        :time="countdown.days"
        label="күн"
        :image="costume"
      />
      <Counter
        v-if="hydrated"
        :time="countdown.hours"
        label="сағат"
        :image="rings"
      />
      <Counter
        v-if="hydrated"
        :time="countdown.minutes"
        label="минут"
        :image="dress"
      />
      <Counter
        v-if="hydrated"
        :time="countdown.seconds"
        label="секунд"
        :image="shoes"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { getTimeDifference } from '@/utils/date';
import costume from '@/assets/images/costume.jpg'
import rings from '@/assets/images/rings.jpg'
import dress from '@/assets/images/dress.jpg'
import shoes from '@/assets/images/shoes.jpg'

const targetDate = new Date('2024-07-27T19:00:00');
const countdown = ref(getTimeDifference(targetDate));
const hydrated = ref(false);

onMounted(() => {
  hydrated.value = true;
  const interval = setInterval(() => {
    countdown.value = getTimeDifference(targetDate);
  }, 1000);

  onUnmounted(() => {
    clearInterval(interval);
  });
});
</script>

<style scoped lang="scss">
.about {
  &-content {
    display: flex;
    justify-content: space-between;
  }
}
</style>
