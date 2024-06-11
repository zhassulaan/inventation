<template>
  <button class="button" @click="action">{{ text }}</button>
</template>

<script setup>
defineProps({
  text: String,
  action: Function
});
</script>

<style scoped>
.button {
  width: 100%;
	height: 48px;
	background-color: var(--clr-white);
	color: var(--clr-primary);
	font-size: 16px;
	font-weight: 600;
	border: 1px solid var(--clr-primary);
	border-radius: 24px;
	margin: 0 auto;
	padding: 0 5%;
}
</style>
