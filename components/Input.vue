<template>
  <input
    type="text"
    class="input"
    :name="name"
    :id="name"
    :class="error ? 'input_error' : 'input_default'"
    :value="value"
  />
</template>

<script setup>
defineProps({
  name: String,
  error: String,
  value: String
});
</script>

<style scoped>
.input {
  width: 100%;
  height: 4.375vh;
  border-radius: 12px;
  padding: 0 5%;
}
</style>
