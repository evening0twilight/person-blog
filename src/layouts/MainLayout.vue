<script setup lang="ts">
import { ref } from 'vue'
import Sidebar from '@/components/common/Sidebar.vue'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}
</script>

<template>
  <div class="main-layout">
    <!-- PC 端侧边栏导航 -->
    <Sidebar class="desktop-sidebar" />

    <!-- 移动端底部导航栏 -->
    <div class="mobile-nav">
      <Sidebar :is-mobile="true" />
    </div>

    <!-- 主内容区域 -->
    <main class="main-content">
      <slot />
    </main>
  </div>
</template>

<style scoped>
.main-layout {
  display: flex;
  min-height: 100vh;
  background: var(--bg-color);
}

.desktop-sidebar {
  display: none;
}

.main-content {
  flex: 1;
  padding: 2rem;
  padding-bottom: 5rem;
  /* 为移动端底部导航留空间 */
  overflow-y: auto;
}

.mobile-nav {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: var(--nav-bg);
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
}

/* PC 端样式 */
@media (min-width: 1024px) {
  .desktop-sidebar {
    display: block;
  }

  .mobile-nav {
    display: none;
  }

  .main-content {
    padding: 3rem;
    padding-bottom: 3rem;
    margin-left: 80px;
    /* 侧边栏宽度 */
  }
}
</style>
