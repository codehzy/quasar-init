<template>
  <!-- 注册form表单 -->
  <q-page-container style="padding: 0">
    <q-page class="q-pa-md">
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <q-input
          filled
          v-model="registerInfo.name"
          label="用户名 *"
          lazy-rules
          maxlength="50"
          :rules="[
            (val) =>
              (val && val.length > 0 && val.length < 50) || '用户名长度应大于1',
          ]"
        />

        <q-input
          filled
          type="password"
          v-model="registerInfo.password"
          label="密码 *"
          maxlength="12"
          lazy-rules
          :rules="[
            (val) => (val !== null && val !== '') || '密码不能为空',
            (val) => (val.length > 6 && val.length < 12) || '请输入6-12位密码',
          ]"
        />

        <q-input
          filled
          v-model="registerInfo.age"
          label="年龄 *"
          lazy-rules
          maxlength="2"
          :rules="[
            (val) => (val !== null && val !== '') || '年龄不能为空',
            (val) => (val > 0 && val < 100) || '请输入你的年龄',
          ]"
        />

        <div>
          <q-btn label="Submit" type="submit" color="primary" />
          <q-btn
            label="Reset"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          />
        </div>
      </q-form>
    </q-page>
  </q-page-container>
</template>

<script lang="ts" setup>
import { reactive } from 'vue';
import { Notify } from 'quasar';
import axios from 'axios';
import { RegisterInfoType } from '../../types/register';

const registerInfo = reactive<RegisterInfoType>({
  name: '',
  age: '',
  password: '',
});

type registerInfoItem = keyof typeof registerInfo;

// 注册
const onSubmit = async () => {
  const {
    data: { name, password, age, code },
  } = await axios.get(
    `https://www.fastmock.site/mock/17bdc755c05894c84e1110fdd3b0c32f/api/register?name=${registerInfo.name}&age=${registerInfo.age}&password=${registerInfo.password}`
  );
  if (code === 200) {
    Notify.create({
      message: '注册成功!',
    });
    localStorage.setItem('user', JSON.stringify({ name, password, age }));
  }
};

/**
 * 重置注册表单
 */
const onReset = () => {
  Object.keys(registerInfo).forEach((key) => {
    registerInfo[key as registerInfoItem] = '';
  });
};
</script>

<style lang="scss" scoped></style>
