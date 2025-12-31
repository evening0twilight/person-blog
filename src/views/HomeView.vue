<script setup lang="ts">
// 博客首页
</script>

<template>
  <div class="home-page">
    <section class="hero">
      <h1 class="hero-title">欢迎来到我的博客</h1>
      <p class="hero-subtitle">分享技术，记录成长</p>
      <!-- TODO: V1.0 实现打字机效果 -->
      <!-- TODO: V1.0 实现粒子背景动画 -->
    </section>

    <!-- TODO: 添加其他板块 -->
  </div>
</template>

<style scoped>
.home-page {
  min-height: 100vh;
}

.hero {
  min-height: 80vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.hero-title {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 1rem;
  background: linear-gradient(45deg, #42b983, #33a06f);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-size: 1.5rem;
  color: var(--text-secondary);
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1rem;
  }
}
</style>
