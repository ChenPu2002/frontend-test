<template>
  <div class="app">
    <!-- Hero Section -->
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <h1 class="title">ColorOS</h1>
          <p class="subtitle">无边界的智能体验</p>
          <p class="description">基于Android深度定制，为全球用户打造流畅、智能、个性化的操作系统</p>
        </div>
      </div>
      <div class="hero-decoration"></div>
    </section>

    <!-- Features Section -->
    <section class="features">
      <div class="container">
        <h2 class="section-title">核心特性</h2>
        <div class="features-grid">
          <div class="feature-card" v-for="feature in features" :key="feature.title">
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3 class="feature-title">{{ feature.title }}</h3>
            <p class="feature-desc">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Design Section -->
    <section class="design">
      <div class="container">
        <h2 class="section-title">设计理念</h2>
        <div class="design-content">
          <div class="design-item" v-for="item in designPrinciples" :key="item.title">
            <h3 class="design-title">{{ item.title }}</h3>
            <p class="design-desc">{{ item.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Technology Section -->
    <section class="technology">
      <div class="container">
        <h2 class="section-title">技术创新</h2>
        <div class="tech-grid">
          <div class="tech-card" v-for="tech in technologies" :key="tech.name">
            <div class="tech-badge">{{ tech.badge }}</div>
            <h3 class="tech-name">{{ tech.name }}</h3>
            <p class="tech-detail">{{ tech.detail }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <p class="footer-text">ColorOS - 让科技更有温度</p>
        <p class="footer-copyright">© 2025 OPPO. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const features = ref([
  {
    icon: '⚡',
    title: '流畅体验',
    description: '采用量子动画引擎3.0，系统响应速度提升45%，带来丝滑流畅的交互体验'
  },
  {
    icon: '🎨',
    title: '个性化定制',
    description: '丰富的主题、壁纸、图标选择，支持AOD息屏显示，让你的手机独一无二'
  },
  {
    icon: '🧠',
    title: '智能助手',
    description: '小布助手深度融合，智能识图、语音操控、智慧推荐，让生活更便捷'
  },
  {
    icon: '🔒',
    title: '隐私保护',
    description: '多层加密保护，隐私安全中心，应用权限精细管理，守护你的数据安全'
  },
  {
    icon: '📱',
    title: '跨屏互联',
    description: '无缝连接手机、平板、手表、电视，多设备协同工作，体验无边界'
  },
  {
    icon: '🔋',
    title: '超级省电',
    description: '智能功耗管理，AI场景识别，续航时间提升30%，持久陪伴你的每一天'
  }
])

const designPrinciples = ref([
  {
    title: '轻盈设计',
    description: '采用无边界设计语言，去繁就简，每一个像素都经过精心打磨，界面清爽舒适，减少视觉负担。'
  },
  {
    title: '灵动交互',
    description: '基于人体工学的手势操作，自然流畅的动画过渡，让每一次触控都成为享受。'
  },
  {
    title: '智能适配',
    description: '深色模式、护眼模式、阅读模式智能切换，根据环境光线自动调节，呵护你的双眼。'
  }
])

const technologies = ref([
  {
    badge: 'AI',
    name: 'ColorOS智能引擎',
    detail: '基于机器学习的AI预测系统，智能分配资源，让常用应用秒开'
  },
  {
    badge: '5G',
    name: '网络加速技术',
    detail: '智能网络切换，游戏、视频专属加速通道，网络体验更稳定'
  },
  {
    badge: '性能',
    name: '量子动画引擎',
    detail: '全新渲染架构，120Hz屏幕完美适配，动画更流畅，功耗更低'
  },
  {
    badge: '安全',
    name: 'TEE安全芯片',
    description: '硬件级加密保护，支付、隐私数据独立存储，安全无忧'
  }
])
</script>

<style scoped>
.app {
  width: 100%;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

/* Hero Section */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.hero-decoration {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 800px;
  height: 800px;
  background: radial-gradient(circle, rgba(59, 130, 246, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  animation: pulse 4s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.5;
  }
  50% {
    transform: translate(-50%, -50%) scale(1.1);
    opacity: 0.8;
  }
}

.hero-content {
  position: relative;
  z-index: 1;
  text-align: center;
}

.title {
  font-size: 6rem;
  font-weight: 700;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, #ffffff 0%, #a0a0a0 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -0.02em;
}

.subtitle {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  color: #e0e0e0;
  font-weight: 300;
}

.description {
  font-size: 1.125rem;
  color: #a0a0a0;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.8;
}

/* Features Section */
.features {
  padding: 120px 0;
  background: linear-gradient(180deg, #000000 0%, #0a0a0a 100%);
}

.section-title {
  font-size: 3rem;
  text-align: center;
  margin-bottom: 4rem;
  font-weight: 600;
  color: #ffffff;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.feature-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  padding: 2.5rem;
  transition: all 0.3s ease;
  cursor: pointer;
}

.feature-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(255, 255, 255, 0.2);
  transform: translateY(-4px);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  display: inline-block;
}

.feature-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #ffffff;
  font-weight: 600;
}

.feature-desc {
  color: #b0b0b0;
  line-height: 1.8;
  font-size: 1rem;
}

/* Design Section */
.design {
  padding: 120px 0;
  background: #000000;
}

.design-content {
  display: grid;
  gap: 3rem;
  max-width: 900px;
  margin: 0 auto;
}

.design-item {
  border-left: 3px solid rgba(255, 255, 255, 0.3);
  padding-left: 2rem;
  transition: all 0.3s ease;
}

.design-item:hover {
  border-left-color: #ffffff;
}

.design-title {
  font-size: 1.75rem;
  margin-bottom: 1rem;
  color: #ffffff;
  font-weight: 600;
}

.design-desc {
  color: #b0b0b0;
  line-height: 1.8;
  font-size: 1.0625rem;
}

/* Technology Section */
.technology {
  padding: 120px 0;
  background: linear-gradient(180deg, #000000 0%, #0a0a0a 100%);
}

.tech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.tech-card {
  background: linear-gradient(135deg, rgba(59, 130, 246, 0.1) 0%, rgba(139, 92, 246, 0.1) 100%);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  padding: 2.5rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.tech-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, #3b82f6, #8b5cf6);
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

.tech-card:hover::before {
  transform: scaleX(1);
}

.tech-card:hover {
  transform: translateY(-4px);
  border-color: rgba(255, 255, 255, 0.3);
}

.tech-badge {
  display: inline-block;
  background: rgba(255, 255, 255, 0.1);
  color: #ffffff;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
}

.tech-name {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #ffffff;
  font-weight: 600;
}

.tech-detail {
  color: #b0b0b0;
  line-height: 1.8;
  font-size: 1rem;
}

/* Footer */
.footer {
  padding: 4rem 0;
  text-align: center;
  background: #000000;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-text {
  font-size: 1.125rem;
  color: #ffffff;
  margin-bottom: 0.5rem;
}

.footer-copyright {
  color: #666666;
  font-size: 0.875rem;
}

/* Responsive */
@media (max-width: 768px) {
  .title {
    font-size: 3.5rem;
  }

  .subtitle {
    font-size: 1.5rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .features-grid {
    grid-template-columns: 1fr;
  }

  .tech-grid {
    grid-template-columns: 1fr;
  }
}
</style>

