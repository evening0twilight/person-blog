<script setup lang="ts">
import { computed } from 'vue'
import { useRouter, useRoute } from 'vue-router'

interface Props {
  isMobile?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  isMobile: false
})

const router = useRouter()
const route = useRoute()

// 导航项配置
const navItems = [
  { name: 'home', path: '/', icon: '🏠', label: '首页' },
  { name: 'skills', path: '/skills', icon: '💡', label: '技能' },
  { name: 'projects', path: '/projects', icon: '📦', label: '作品' },
  { name: 'demo', path: '/demo', icon: '🎮', label: 'Demo' },
  { name: 'about', path: '/about', icon: '👤', label: '关于' },
]

const isActive = (path: string) => {
  return route.path === path
}

const handleNavigate = (path: string) => {
  router.push(path)
}
</script>

<template>
  <nav :class="['sidebar', { 'sidebar-mobile': isMobile }]">
    <div class="nav-items">
      <div v-for="item in navItems" :key="item.name" :class="['nav-item', { active: isActive(item.path) }]"
        @click="handleNavigate(item.path)">
        <span class="nav-icon">{{ item.icon }}</span>
        <span class="nav-label">{{ item.label }}</span>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.sidebar {
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  width: 80px;
  background: var(--sidebar-bg, #1a1a1a);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem 0;
  z-index: 1000;
}

.sidebar-mobile {
  position: relative;
  height: auto;
  width: 100%;
  flex-direction: row;
  padding: 0;
}

.nav-items {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  width: 100%;
}

.sidebar-mobile .nav-items {
  flex-direction: row;
  justify-content: space-around;
  padding: 0.5rem 0;
}

.nav-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  color: var(--text-secondary, #888);
}

.sidebar-mobile .nav-item {
  padding: 0.75rem 0.5rem;
  flex: 1;
}

.nav-item:hover {
  color: var(--text-primary, #fff);
  transform: scale(1.1);
}

.sidebar-mobile .nav-item:hover {
  transform: scale(1.05);
}

.nav-item.active {
  color: var(--primary-color, #42b983);
}

.nav-item.active::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 4px;
  height: 60%;
  background: var(--primary-color, #42b983);
  border-radius: 0 4px 4px 0;
}

.sidebar-mobile .nav-item.active::before {
  left: 50%;
  top: 0;
  transform: translateX(-50%);
  width: 60%;
  height: 3px;
  border-radius: 0 0 4px 4px;
}

.nav-icon {
  font-size: 1.5rem;
  transition: transform 0.3s ease;
}

.nav-item:hover .nav-icon {
  transform: scale(1.2);
}

.nav-label {
  font-size: 0.75rem;
  font-weight: 500;
  white-space: nowrap;
  opacity: 0;
  max-height: 0;
  overflow: hidden;
  transition: all 0.3s ease;
}

.nav-item:hover .nav-label,
.nav-item.active .nav-label,
.sidebar-mobile .nav-label {
  opacity: 1;
  max-height: 20px;
}

.sidebar-mobile .nav-label {
  font-size: 0.7rem;
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
