<template>
  <a-layout style="width: auto;">
    <a-layout-header>Header</a-layout-header>
    <a-layout-content style="margin: 0 10%; min-width: 1000px;">
      <App />
    </a-layout-content>
    <a-layout-footer>Footer</a-layout-footer>
  </a-layout>
</template>

<script setup>
import App from "./App.vue";
</script>

<style scoped></style>
