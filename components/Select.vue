<template>
  <div class="select">
    <label :for="name" class="select-label" >{{ label }}</label>
    <span
      v-for="option in options"
      :key="option.id"
      class="select-option"
      @click="() => selectItem(option)"
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
  name: String,
  label: String,
  options: Array,
  value: Object,
  error: String
});
const emit = defineEmits(["select"]);

function selectItem(item) {
	emit("select", item);
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.select {
  @include col;
  &-label {
    @include label;
  }
  &-option {
    display: flex;
    gap: 16px;
    margin-top: 6px;
    &__input:after,
    &__input:checked:after {
      position: relative;
      content: "";
      bottom: -3px;
      left: -1px;
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
      left: 4px;
      width: 5px;
      height: 5px;
      box-shadow: 0 0 0 2px var(--clr-green), 0 0 0 4px white, 0 0 0 5px var(--clr-green);
    }
    &__error {
      color: var(--clr-red);
      text-decoration: underline;
    }
	}
}
</style>