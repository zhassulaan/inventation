<template>
  <div class="modal">
    <div class="background" @click="closeModal"></div>
    <div class="body">
      <div class="body-close" @click="closeModal">
        <span class="body-close__icon"></span>
      </div>
        <p v-if="error_text" class="body-text body-text_error">{{ error_text }}</p>
        <p v-else class="body-text body-text_default">{{ text }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  text: String,
  error_text: String
});
const emit = defineEmits(["closeModal"]);

function closeModal() {
  emit("closeModal");
};
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.modal {
  position: fixed;
	top: 0;
	left: 0;
	width: 100vw;
	height: 100vh;
	z-index: 3;
	.background {
		@include origin;
		top: 0;
		left: 0;
		@include background;
		z-index: 4;
	}
	.body {
		@include center;
		width: 75%;
		height: 20%;
		background-color: var(--clr-white);
		border-radius: 12px;
		z-index: 5;
		&-text {
			@include center_block;
			width: 80%;
			height: 100%;
			font-size: 20px;
			font-weight: 600;
			margin: auto;
			&_error {
				color: var(--clr-red);
			}
			&_default {
				color: var(--clr-green);
			}
		}
		&-close {
			position: absolute;
			display: inline-block;
			width: 20px;
			height: 20px;
			top: 10px;
			right: 10px;
			&__icon,
			&__icon::before,
			&__icon::after {
				position: absolute;
				display: block;
				width: 100%;
				height: 1.5px;
				background-color: var(--clr-black);
			}
			&__icon {
				top: 50%;
				transform: rotate(45deg);
				&::before,
				&::after {
					content: "";
				}
				&::before {
					top: -8px;
					transform: rotate(-90deg) translate(-8px, 0);
				}
				&::after {
					bottom: -8px;
					transform: rotate(-90deg) translate(8px, 0);
				}
			}
		}
	}
}
</style>

