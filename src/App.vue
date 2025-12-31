<script setup lang="ts">
import { RouterView } from 'vue-router'
import MainLayout from '@/layouts/MainLayout.vue'
</script>

<template>
  <MainLayout>
    <RouterView />
  </MainLayout>
</template>

<style>
/* 全局样式重置 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  background: var(--bg-color);
  color: var(--text-primary);
}

/* 主题变量 */
:root {
  --sidebar-bg: #1a1a1a;
  --nav-bg: #1a1a1a;
  --text-primary: #ffffff;
  --text-secondary: #888888;
  --primary-color: #42b983;
  --bg-color: #0f0f0f;
}
</style>
