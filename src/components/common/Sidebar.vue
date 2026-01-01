<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

interface Props {
  isMobile?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  isMobile: false
})

// 导航项配置 - 基于锚点ID
const navItems = [
  { id: 'home', icon: '🏠', label: '首页' },
  { id: 'skills', icon: '💡', label: '技能' },
  { id: 'projects', icon: '📦', label: '作品' },
  { id: 'demo', icon: '🎮', label: 'Demo' },
  { id: 'about', icon: '👤', label: '关于' },
]

const activeSection = ref('home')

// 滚动到指定区域
const handleNavigate = (id: string) => {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

// 监听滚动，更新当前激活的区域
const handleScroll = () => {
  const sections = navItems.map(item => ({
    id: item.id,
    element: document.getElementById(item.id)
  })).filter(section => section.element !== null)

  const scrollPosition = window.scrollY + window.innerHeight / 2

  for (let i = sections.length - 1; i >= 0; i--) {
    const section = sections[i]
    if (section?.element && section.element.offsetTop <= scrollPosition) {
      activeSection.value = section.id
      break
    }
  }
}

const isActive = (id: string) => {
  return activeSection.value === id
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll() // 初始化
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav :class="['sidebar', { 'sidebar-mobile': isMobile }]">
    <div class="nav-items">
      <div v-for="item in navItems" :key="item.id" :class="['nav-item', { active: isActive(item.id) }]"
        @click="handleNavigate(item.id)">
        <span class="nav-icon">{{ item.icon }}</span>
        <span class="nav-label">{{ item.label }}</span>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.sidebar {
  position: fixed;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  height: 50vh;
  width: 60px;
  background: var(--sidebar-bg, rgba(26, 26, 26, 0.8));
  backdrop-filter: blur(10px);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1.5rem 0;
  border-radius: 30px;
  z-index: 1000;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
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
  flex-direction: row;
  align-items: center;
  gap: 0.5rem;
  padding: 0.8rem;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  color: var(--text-secondary, #888);
  border-radius: 12px;
  width: 100%;
  justify-content: center;
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

.nav-item.active {
  background: rgba(66, 185, 131, 0.1);
}

.nav-item.active::before {
  content: '';
  position: absolute;
  right: -10px;
  top: 50%;
  transform: translateY(-50%);
  width: 4px;
  height: 60%;
  background: var(--primary-color, #42b983);
  border-radius: 4px 0 0 4px;
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
  font-size: 0.85rem;
  font-weight: 500;
  white-space: nowrap;
  position: absolute;
  right: 70px;
  background: var(--sidebar-bg, rgba(26, 26, 26, 0.95));
  padding: 0.5rem 1rem;
  border-radius: 8px;
  opacity: 0;
  pointer-events: none;
  transform: translateX(10px);
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
}

.nav-item:hover .nav-label {
  opacity: 1;
  transform: translateX(0);
}

.sidebar-mobile .nav-label {
  position: static;
  opacity: 1;
  transform: none;
  background: transparent;
  padding: 0;
  box-shadow: none;
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
