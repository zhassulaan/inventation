<template>
  <div class="modal">
    <div class="modal-background" @click="closeModal"></div>

    <div v-if="alert" class="modal-body">
			<Button :text="text" @click="closeModal" />
    </div>

    <div v-else class="modal-body">
      <div class="close" @click="closeModal">
        <span class="close-icon"></span>
      </div>

			<p v-if="error_text" class="text text-error">{{ error_text }}</p>
			<p v-else class="text text-default">{{ text }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  text: String,
  error_text: String,
  alert: Boolean
});
const emit = defineEmits(["closeModal"]);

function closeModal() {
  emit("closeModal");
	document.body.style.overflow = "auto";
};

onMounted(() => {
  document.body.style.overflow = 'hidden';
});
onBeforeUnmount(() => {
  document.body.style.overflow = 'auto';
});
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.modal {
	@include origin;
  position: fixed;
	@include fullpage;
	z-index: 3;
	&-background {
		@include origin;
		@include background;
		z-index: 3;
	}
	&-body {
		@include center;
		z-index: 4;
		width: 75%;
		height: 20%;
		border-radius: 12px;
		background-color: var(--clr-white);
		.close {
			position: absolute;
			width: 20px;
			height: 20px;
			top: 10px;
			right: 10px;
			&-icon,
			&-icon::before,
			&-icon::after {
				position: absolute;
				width: 100%;
				height: 1.5px;
				background-color: var(--clr-black);
			}
			&-icon {
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
		.button {
			@include center;
			width: 60%;
			margin: auto;
		}
		.text {
			@include center_block;
			width: 80%;
			height: 100%;
			font-size: 18px;
			font-weight: 500;
			margin: auto;
			&-error {
				color: var(--clr-red);
			}
			&-default {
				color: var(--clr-green);
			}
		}
	}
}
</style>

