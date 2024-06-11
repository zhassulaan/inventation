<template>
  <div class="input">
    <label :for="name" class="input-label" >{{ label }}</label>
    <input
      type="text"
      class="input-text"
      :name="name"
      :id="name"
      :class="{ 'input-text_error': error }"
      :value="value"
    />
  </div>
</template>

<script setup>
defineProps({
  name: String,
  label: String,
  error: String,
  value: String
});
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.input {
  @include col;
  &-label {
    @include label;
  }
  &-text {
    width: 100%;
    height: 48px;
    padding: 0 12px;
    font-size: 16px;
    color: var(--clr-primary);
    border: 1px solid var(--clr-primary);
    border-radius: 16px;
    outline: none;
    &:focus {
      border: 1px solid var(--clr-green);
    }
    &_error {
      border: 1px solid var(--clr-red);
    }
  }
}
</style>
