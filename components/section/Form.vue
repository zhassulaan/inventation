<template>
  <div id="form">
    <h4>Анкета</h4>
    <div class="form">
      <div class="form-background"></div>
      <p class="form-text">Тіркелуші қонақтың жасы 16-дан жоғары болуы тиіс</p>

      <div class="form-input">
        <p class="form-input__label">Аты-жөніңіз</p>
        <Input name="first_fullname" :value="firstName" @input="e => firstName = e.target.value" :error="error" />
      </div>

      <div class="form-input">
        <p class="form-input__label">Жұбайыңыздың аты-жөні (егер болса)</p>
        <Input name="second_fullname" :value="secondName" @input="e => secondName = e.target.value" :error="error" />
      </div>

      <div class="form-input">
        <p class="form-input__label">Тойға келесіз бе?</p>
        <Select :error="error" :options="visitOptions" :value="visit" @select="setVisit" />
      </div>

      <Button text="Жіберу" @click="submit" />
      <p class="form-body__text">Қонақ санын нақты есептей алуымыз үшін анкетаны бір-ақ рет толтырыңызды сұраймыз!</p>
    </div>
    <Modal v-if="modal" :text="message" :error_text="error" @closeModal="close" />
  </div>
</template>

<script setup>
import emailjs from "emailjs-com";

const firstName = ref("");
const secondName = ref("");
const visit = ref(null);
const error = ref("");
const message = ref("");
const modal = ref(false);
const visitOptions = [
  { id: "yes", text: "Иә, әрине" },
  { id: "no", text: "Өкінішке орай келе алмаймын" }
];

function setVisit(option) {
  visit.value = option;
}
function submit() {
  if (firstName.value === "" || secondName.value === "" || !visit.value) {
    error.value = "Барлығын дұрыстап толтырыңыз";
    modal.value = true;
  } else {
    error.value = "";
    message.value = "Форма сәтті жіберілді!";
    modal.value = true;
    const params = {
      first_name: firstName.value,
      second_name: secondName.value,
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
  secondName.value = "";
  visit.value = null;
  document.body.style.overflow = "auto";
}
</script>

<style scoped lang="scss">
@use "@/assets/styles/mixins" as *;

.form {
  position: relative;
  padding: 2.875vh 5%;
  &-background {
    @include origin;
    width: 100%;
    height: 100%;
    background-color: var(--clr-green);
    border-radius: 16px;
    opacity: .45;
    z-index: -1;
  }
  &-text {
    text-decoration: underline;
    font-size: 12px;
    padding: 1.5vh 0;
  }
  &-input {
    margin-bottom: 3.875vh;
    &__label {
      font-weight: 600;
      margin-bottom: 1.125vh;
    }
  }
}
</style>
