<template>
  <div id="about" class="home-content main">

    <div class="about-content">
      <Counter
        v-if="hydrated"
        v-for="(item, idx) in data"
        :key="idx"
        :time="item.time"
        :label="item.label"
        :image="item.image"
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
const data = [
  {
    time: countdown.days,
    label: 'күн',
    image: costume
  }, {
    time: countdown.hours,
    label: 'сағат',
    image: rings
  }, {
    time: countdown.minutes,
    label: 'минут',
    image: dress
  }, {
    time: countdown.seconds,
    label: 'секунд',
    image: shoes
  }
];

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
