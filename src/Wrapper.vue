<template>
  <a-layout style="width: auto">
    <a-layout-header style="text-align: right">
      <a-space>
        <a-link @click="handleClick('login')">login</a-link>

        <a-link @click="handleClick('register')">register</a-link>
      </a-space>
    </a-layout-header>
    <a-layout-content style="margin: 0 10%; min-width: 1000px">
      <App />
    </a-layout-content>
    <a-layout-footer>Footer</a-layout-footer>
  </a-layout>
  <a-modal
    v-model:visible="visible"
    title="Modal Form"
    @cancel="handleCancel"
    @before-ok="handleBeforeOk"
  >
    <a-form :model="form" :style="{ width: '600px' }" @submit="handleSubmit">
      <a-form-item field="name" tooltip="输入有效的账户名" label="账户名">
        <a-input v-model="form.name" placeholder="账号名称" />
      </a-form-item>
      <a-form-item field="sex" label="性别">
        <a-select v-model="form.sex" placeholder="选择性别">
          <a-option>男</a-option>
          <a-option>女</a-option>
          <a-option>其他</a-option>
        </a-select>
      </a-form-item>
      <a-form-item field="password" label="密码">
        <a-input-password
          v-model="form.password"
          :style="{ width: '320px' }"
          placeholder="Please enter something"
          allow-clear
        />
      </a-form-item>
      <a-form-item field="isRead">
        <a-checkbox v-model="form.isRead"> I have read the manual </a-checkbox>
      </a-form-item>
      <a-form-item>
        <a-space>
          <a-button html-type="submit">Login</a-button>
          <a-button html-type="submit">Register</a-button>
        </a-space>
      </a-form-item>
    </a-form>
  </a-modal>
</template>

<script setup>
import { ref, reactive } from "vue";
import App from "./App.vue";

const visible = ref(false);
const form = reactive({
  name: "",
  post: "",
  password: "",
  isRead: false,
});

const handleClick = () => {
  visible.value = true;
};
const handleCancel = () => {
  visible.value = false;
};
const handleBeforeOk = (done) => {
  console.log(form);
  window.setTimeout(() => {
    done();
    // prevent close
    // done(false)
  }, 3000);
};
</script>

<style scoped></style>
