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
          :class="[
            'calendar-week__day',
            { active: day === activeDay }
          ]"
        >
          {{ day }}
          <font-awesome-icon v-if="day === activeDay" icon="heart" class="active-icon" />
        </span>
      </div>
    </client-only>
  </div>
</template>

<script setup>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { library } from "@fortawesome/fontawesome-svg-core";
import { faHeart } from "@fortawesome/free-solid-svg-icons";

library.add(faHeart);

const weekdayNames = ref(["Пн", "Вт", "Ср", "Чт", "Пт", "Сб", "Вс"]);
const activeDay = ref(27);
const date = ref(new Date());
const firstDay = ref(new Date(date.value.getFullYear(), 6, 1));
const lastDay = ref(new Date(date.value.getFullYear(), 6 + 1, 0));
const daysCount = ref(lastDay.value.getDate());
const firstDayOfWeek = ref(firstDay.value.getDay());

const calendar = computed(() => {
  const weeks = [];
  let week = [];
  for (let i = 1; i < firstDayOfWeek.value; i++) {
    week.push("");
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

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

@keyframes pulse {
  0% {
		top: -25%;
		left: -25%;
		width: 150%;
		height: 150%;
	} 50% {
		top: -40%;
		left: -40%;
		width: 180%;
		height: 180%;
	} 100% {
		top: -25%;
		left: -25%;
		width: 150%;
		height: 150%;
	}
}

.calendar {
  margin: 0 auto;
  &-header,
  &-week {
    display: flex;
    gap: 16px;
  }
	&-header {
		margin-bottom: 20px;
		padding-bottom: 10px;
		border-bottom: 1px solid var(--clr-grey);
	}
  &-week {
    margin-top: 16px;
    &__day {
      @include center_block;
      &.active {
        color: var(--clr-white);
      }
    }
    .active {
      position: relative;
      &-icon {
        position: absolute;
        color: var(--clr-gold);
        z-index: -1;
        animation: pulse 1.25s infinite;
      }
    }
  }
	&-header__label,
	&-week__day {
		width: 21px;
    color: var(--clr-primary);
	}
}
</style>
