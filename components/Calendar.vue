<template>
  <div class="calendar">
    <div class="calendar-header">
      <p
        v-for="(name, idx) in weekdayNames"
        :key="idx"
        class="calendar-header__label"
      >
        {{ name }}
      </p>
    </div>
    <client-only>
      <div v-for="(week, weekIdx) in calendar" :key="weekIdx" class="calendar-week">
        <span
          v-for="(day, dayIdx) in week"
          :key="dayIdx"
          :class="['calendar-week__day', { active: day === activeDay }]"
        >
          {{ day }}
          <font-awesome-icon v-if="day === activeDay" icon="heart" class="active-icon" />
        </span>
      </div>
    </client-only>
  </div>
</template>

<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { library } from '@fortawesome/fontawesome-svg-core';
import { faHeart } from '@fortawesome/free-solid-svg-icons';
import '@fortawesome/fontawesome-svg-core/styles.css';
import '../assets/styles/calendar.scss';

library.add(faHeart);

const weekdayNames = ref(['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс']);
const activeDay = ref(12);
const date = ref(new Date());
const firstDay = ref(new Date(date.value.getFullYear(), 7, 1));
const lastDay = ref(new Date(date.value.getFullYear(), 7 + 1, 0));
const daysCount = ref(lastDay.value.getDate());
const firstDayOfWeek = ref(firstDay.value.getDay());

const calendar = computed(() => {
  const weeks = [];
  let week = [];
  for (let i = 1; i < firstDayOfWeek.value; i++) {
    week.push('');
  }
  for (let day = 1; day <= daysCount.value; day++) {
    if (week.length === 7) {
      weeks.push(week);
      week = [];
    }
    week.push(day);
  }
  weeks.push(week);
  return weeks;
});
</script>
