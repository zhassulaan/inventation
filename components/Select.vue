<template>
  <div class="select">
    <span
      v-for="option in options"
      :key="option.id"
      @click="() => selectItem(option)"
      class="select-option"
    >
      <input
        type="radio"
        :id="option.id"
        name="option"
        :value="option.id"
        class="select-option__input"
        :checked="option.id === value?.id"
      />
      <p :class="{ 'select-option__error': error }">{{ option.text }}</p>
    </span>
  </div>
</template>

<script setup>
defineProps({
  options: Array,
  error: String,
  value: Object,
  action: Function
});
const emit = defineEmits(["select"]);

function selectItem(item) {
	emit("select", item);
}
</script>

<style scoped lang="scss">
.select {
  display: flex;
	flex-direction: column;
	gap: 1vh;
  &-option {
    text-align: start;
    display: flex;
    gap: 3%;
    &__input:after,
    &__input:checked:after {
      position: relative;
      content: '';
      bottom: -2px;
      left: -2px;
      display: inline-block;
      visibility: visible;
      width: 15px;
      height: 15px;
      border-radius: 50%;
      border: 1px solid var(--clr-green);
      padding: 1px;
    }
    &__input:after {
      background-color: var(--clr-white);
    }
    &__input:checked:after {
      left: 0;
      width: 9px;
      height: 9px;
      box-shadow: 0 0 0 2px var(--clr-green), 0 0 0 4px white, 0 0 0 5px var(--clr-green);
    }
    &__error {
      color: var(--clr-red);
      text-decoration: underline;
    }
	}
}
</style>