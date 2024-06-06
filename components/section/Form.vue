<template>
  <div id="form" class="home-content form">
    <h2 class="home-content__title">Анкета</h2>
    <div class="form-body">
      <div class="form-body__background"></div>
      <p class="form-body__text">Тіркелуші қонақтың жасы 16-дан жоғары болуы тиіс</p>
      <div class="form-body__input">
        <p class="form-body__input-label">Аты-жөніңіз</p>
        <Input name="first_fullname" :value="firstName" @input="e => firstName = e.target.value" :error="error" />
      </div>
      <div class="form-body__input">
        <p class="form-body__input-label">Жұбайыңыздың аты-жөні (егер болса)</p>
        <Input name="second_fullname" :value="secondName" @input="e => secondName = e.target.value" :error="error" />
      </div>
      <div class="form-body__input">
        <p class="form-body__input-label">Тойға келесіз бе?</p>
        <Select :error="error" :options="visitOptions" :value="visit" @select="setVisit" />
      </div>
      <Button text="Жіберу" @click="submit" />
      <p class="form-body__text">Қонақ санын нақты есептей алуымыз үшін анкетаны бір-ақ рет толтырыңызды сұраймыз</p>
    </div>
    <Modal v-if="modal" :text="message" :error_text="error" @closeModal="close" />
  </div>
</template>

<script setup>
import emailjs from 'emailjs-com';

const firstName = ref('');
const secondName = ref('');
const visit = ref(null);
const error = ref('');
const message = ref('');
const modal = ref(false);
const visitOptions = [
  { id: 'yes', text: 'Иә, әрине' },
  { id: 'no', text: 'Өкінішке орай келе алмаймын' }
];

function setVisit(option) {
  visit.value = option;
}
function submit() {
  if (firstName.value === '' || secondName.value === '' || !visit.value) {
    error.value = 'Барлығын дұрыстап толтырыңыз';
    modal.value = true;
  } else {
    error.value = '';
    message.value = 'Форма сәтті жіберілді!';
    modal.value = true;
    const params = {
      first_name: firstName.value,
      second_name: secondName.value,
      visit: visit.value.text
    };
    emailjs.send('service_ellnze8', 'template_vg9f4xb', params, 'yVKttaYJiGixIKUis')
      .then(res => {
        console.log('success', res.status);
      });
  }
}
function close() {
  modal.value = false;
  error.value = '';
  message.value = '';
  firstName.value = '';
  secondName.value = '';
  visit.value = null;
}
</script>
