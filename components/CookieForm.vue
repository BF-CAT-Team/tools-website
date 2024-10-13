```vue
<template>
  <a-form @submit="handleSubmit">
    <a-form-item label="账号">
      <a-input v-model="account"/>
    </a-form-item>
    <a-form-item label="密码">
      <a-input type="password" v-model="password"/>
    </a-form-item>
    <a-form-item label="密钥">
      <a-input v-model="secret"/>
    </a-form-item>
    <a-form-item label="验证码">
      <a-input v-model="captcha"/>
    </a-form-item>
    <a-form-item>
      <a-button type="primary" html-type="submit">提交</a-button>
    </a-form-item>
  </a-form>
</template>

<script setup>
import { ref } from 'vue';

const account = ref('');
const password = ref('');
const secret = ref('');
const captcha = ref('');

const handleSubmit = () => {
  console.log('账号:', account.value);
  console.log('密码:', password.value);
  console.log('密钥:', secret.value);
  console.log('验证码:', captcha.value);
};
</script>
```