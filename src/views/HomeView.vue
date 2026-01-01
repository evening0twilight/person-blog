<script setup lang="ts">
// 单页滚动博客
</script>

<template>
  <div class="home-page">
    <!-- 首页区域 -->
    <section id="home" class="section hero-section">
      <h1 class="hero-title">欢迎来到我的博客</h1>
      <p class="hero-subtitle">分享技术，记录成长</p>
      <!-- TODO: V1.0 实现打字机效果 -->
      <!-- TODO: V1.0 实现粒子背景动画 -->
    </section>

    <!-- 技能区域 -->
    <section id="skills" class="section skills-section">
      <div class="section-content">
        <h2 class="section-title">我的技能</h2>
        <p class="section-text">技能展示区域 - 待实现静态标签云</p>
        <!-- TODO: V1.0 实现静态标签云或列表 -->
        <!-- TODO: V2.0 实现 3D 技能树 -->
      </div>
    </section>

    <!-- 作品区域 -->
    <section id="projects" class="section projects-section">
      <div class="section-content">
        <h2 class="section-title">我的作品</h2>
        <p class="section-text">作品集展示区域 - 四次作品赛作品</p>
        <!-- TODO: V1.0 实现作品卡片展示，支持翻转/放大效果 -->
      </div>
    </section>

    <!-- Demo 区域 -->
    <section id="demo" class="section demo-section">
      <div class="section-content">
        <h2 class="section-title">Demo 展示</h2>
        <p class="section-text">各类小 Demo 展示区域</p>
        <!-- TODO: V3.0 实现 Canvas 动画、数据可视化、工具等 Demo -->
      </div>
    </section>

    <!-- 关于区域 -->
    <section id="about" class="section about-section">
      <div class="section-content">
        <h2 class="section-title">关于我</h2>
        <p class="section-text">个人介绍、联系方式等内容</p>
        <!-- TODO: 实现个人介绍、联系方式等内容 -->
      </div>
    </section>
  </div>
</template>

<style scoped>
.home-page {
  width: 100%;
}

.section {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 4rem 2rem;
  scroll-margin-top: 0;
}

/* 首页区域样式 */
.hero-section {
  text-align: center;
}

.hero-title {
  font-size: 3.5rem;
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

/* 其他区域通用样式 */
.section-content {
  max-width: 1200px;
  width: 100%;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  color: var(--text-primary);
  text-align: center;
}

.section-text {
  font-size: 1.2rem;
  color: var(--text-secondary);
  text-align: center;
}

/* 区域背景区分 */
.skills-section {
  background: linear-gradient(180deg, var(--bg-color) 0%, rgba(66, 185, 131, 0.05) 100%);
}

.projects-section {
  background: var(--bg-color);
}

.demo-section {
  background: linear-gradient(180deg, var(--bg-color) 0%, rgba(66, 185, 131, 0.03) 100%);
}

.about-section {
  background: var(--bg-color);
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .section-text {
    font-size: 1rem;
  }

  .section {
    padding: 3rem 1.5rem;
  }
}
</style>
