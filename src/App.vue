<script setup lang="ts">
import Header from './components/Header.vue';
import Input from './components/ui/Input.vue';
import Button from './components/ui/Button.vue';
import logo from './assets/logo.svg'
import { ref } from 'vue';
const login = ref('')
const password = ref('')
const tryLogin = () => {
  if (login.value === '87778882288' && password.value === '111111') window.location.replace('https://shop.pb-vip.com/#/')
}
</script>

<template>
  <div class="w-screen h-screen flex flex-col bg">
    <Header />
    <div class="flex-grow flex flex-col px-6 w-full max-w-[400px] m-auto">
      <div class="w-full flex justify-center pt-7 pb-12">
        <img class="w-[78px]" :src="logo" alt="logo" />
      </div>
      <div class="flex flex-col gap-[22px]">
        <Input icon="phone" placeholder="ID, email или номер тел. " :value="login" @change="(value) => login = value" />
        <Input icon="lock" type="password" placeholder="Пароль" :value="password" @change="(value) => password = value" />
        <Button variant="filled" @click="tryLogin">Войти</Button>
      </div>
      <div class="pt-3 flex flex-col items-center">
        <div class="max-w-320px text-center">
          <span class="text-[#898A8D] text-[14px] leading-[1.3]">Нажимая “Войти” вы принимаете<br/><a target="_blank" href="#" class="text-[#257AD7] underline">пользовательское соглашение</a></span>
        </div>
      </div>
      <div class="flex-grow flex w-full items-end pb-[38px]">
        <div class="flex flex-col items-center w-full gap-6">
          <Button class="w-full" variant="outlined">Зарегистрироваться</Button>
          <span class="opacity-50 text-[#1D1E20]">Copyright 2021 辽宁未来生物科技有限公司</span>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.bg {
  background-image: url('bg.svg');
  background-repeat: no-repeat;
  background-position: 50px 50px;
  background-size: cover;
}
</style>


