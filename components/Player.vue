<template>
  <div class="player">
    <div v-if="isPlaying" class="player-stop" @click="stopAudio">
      <span class="player-stop__icon"></span>
    </div>
    <div v-else class="player-start" @click="playAudio">
      <span class="player-start__icon"></span>
    </div>
  </div>
</template>

<script setup>
import { Howl } from "howler";
import music from "@/assets/music.mp3";

const firstTime = ref(true);
const isPlaying = ref(false);
const audio = ref(null);
const audioPosition = ref(0);

function playAudio() {
  isPlaying.value = true;
  const sound = new Howl({
    src: [music],
		loop: true,
    onload: () => {
      sound.seek(audioPosition.value);
      sound.play();
    },
  });
  audio.value = sound;
}
function stopAudio() {
  isPlaying.value = false;
  if (audio.value) {
    audioPosition.value = audio.value.seek();
    audio.value.stop();
  }
}
function handleScroll() {
  if (firstTime.value) {
    playAudio();
		firstTime.value = false;
	}
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});
onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.player {
  position: fixed;
  bottom: 10vh;
  right: 10vw;
  z-index: 3;
	&-start,
	&-stop {
		@include center_block;
		width: 40px;
		height: 40px;
		background-color: var(--clr-black);
		border-radius: 50%;
    cursor: pointer;
	}
	&-start {
		transform: rotate(90deg);
		padding-bottom: 5px;
		&__icon {
			position: relative;
			width: 10px;
			height: 10px;
			text-align: left;
			background-color: var(--clr-white);
			border-top-right-radius: 30%;
			transform: rotate(-60deg) skewX(-30deg) scale(1,.866);
			&::before,
			&::after {
				content: "";
				position: absolute;
				width: 10px;
				height: 10px;
				background-color: inherit;
				border-top-right-radius: 30%;
			}
			&::before {
				transform: rotate(-135deg) skewX(-45deg) scale(1.414,.707) translate(0,-50%);
			}
			&::after {
				transform: rotate(135deg) skewY(-45deg) scale(.707,1.414) translate(50%);
			}
		}
	}
	&-stop {
		position: relative;
		&__icon {
			&::before,
			&::after {
				position: absolute;
				content: "";
				top: 50%;
				width: 3px;
				height: 16px;
				background-color: var(--clr-white);
				border-radius: 5%;
				transform: translateY(-50%);
			}
			&::before {
				left: 14px;
			}
			&::after {
				right: 14px;
			}
		}
	}
}
</style>
