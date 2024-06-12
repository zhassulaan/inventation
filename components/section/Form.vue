<template>
  <div class="form">
    <div>
      <h5>Тойға қатысуыңызды растауыңызды сұраймыз:</h5>
      <p class="form-text red">Тіркелуші қонақтың жасы 16-дан жоғары болуы тиіс</p>
    </div>

    <Input
      name="first_fullname"
      label="Аты-жөніңіз"
      :value="firstName"
      :error="error"
      @input="e => firstName = e.target.value"
    />
    <Select
      name="visit"
      label="Тойға келесіз бе?"
      :options="visitOptions"
      :value="visit"
      :error="error"
      @select="setVisit"
    />

    <div>
      <Button text="Жіберу" @click="submit" />
      <p id="alert" class="form-text red">Тойға баласыз келуіңізді сұраймыз! Орын саны шектеулі!</p>
      <p class="form-text">Қонақ санын нақты есептей алуымыз үшін анкетаны бір-ақ рет толтырыңыз!</p>
    </div>
    <Modal v-if="modal" :text="message" :error_text="error" @closeModal="close" />
  </div>
</template>

<script setup>
import emailjs from "emailjs-com";

const firstName = ref("");
const visit = ref(null);
const error = ref("");
const message = ref("");
const modal = ref(false);
const visitOptions = [
  { id: "single", text: "Иә, әрине келемін" },
  { id: "pair", text: "Жұбайыммен келемін" },
  { id: "no", text: "Өкінішке орай келе алмаймын" }
];

function setVisit(option) {
  visit.value = option;
}
function submit() {
  if (firstName.value === "" || !visit.value) {
    error.value = "Барлығын дұрыстап толтырыңыз";
    modal.value = true;
  } else {
    error.value = "";
    message.value = "Форма сәтті жіберілді!";
    modal.value = true;
    const params = {
      first_name: firstName.value,
      visit: visit.value.text
    };
    emailjs.send("service_ellnze8", "template_vg9f4xb", params, "yVKttaYJiGixIKUis")
      .then(res => {
        console.log("success", res.status);
      });
  }
  document.body.style.overflow = "hidden";
}
function close() {
  modal.value = false;
  error.value = "";
  message.value = "";
  firstName.value = "";
  visit.value = null;
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.form {
  @include col;
  gap: 32px;
  &-text {
    font-size: 12px;
    text-decoration: underline;
    margin-top: 6px;
    &.red {
      color: var(--clr-red);
    }
    &#alert {
      font-size: 16px;
      margin-top: 12px;
    }
  }
}
</style>
