<template>
  <div class="display">
  <a-form
    :model="formState"
    name="basic"
    :label-col="{ span: 10}"
    :wrapper-col="{ span: 20 }"
    autocomplete="off"
    @finish="onFinish"
    @finishFailed="onFinishFailed"
  >
    <a-form-item
      label="用户名"
      name="username"
      :rules="[{ required: true, message: '请输入你的用户名' }]"
      
    >
      <a-input v-model:value="formState.username" />
    </a-form-item>

    <a-form-item
      label="密码"
      name="password"
      :rules="[{ required: true, message: '请输入你的密码' }]"
    >
      <a-input-password v-model:value="formState.password" />
    </a-form-item>

    <a-form-item  name="remember" :wrapper-col="{ offset: 8, span: 20}">
      <a-checkbox v-model:checked="formState.remember">七天免登陆</a-checkbox>
    </a-form-item>

    <a-form-item :wrapper-col="{ offset: 8, span: 20}">
      <a-button type="primary" html-type="submit">登陆</a-button>
    </a-form-item>
  </a-form>
 </div>
</template>

<style>
.display {
  position: absolute;
      top: 33.33%;
      left: 33.33%;
      transform: translate(-50%, -50%);
      width: 500px; /* 设置表单宽度 */
      height: 200px; /* 设置表单高度 */
}
</style>

<script setup>
import { reactive } from 'vue';
const formState = reactive({
  username: '',
  password: '',
  remember: true,
});
const onFinish = values => {
  console.log('登陆成功:', values);
};
const onFinishFailed = errorInfo => {
  console.log('登陆失败:', errorInfo);
};
</script>

