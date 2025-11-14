<template>
  <div class="app">
    <!-- Floating Particles Background -->
    <div class="particles">
      <div class="particle" v-for="i in 20" :key="i" :style="getParticleStyle(i)"></div>
    </div>

    <!-- Hero Section -->
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <h1 class="title fade-in-up">ColorOS</h1>
          <p class="subtitle fade-in-up delay-1">无边界的智能体验</p>
          <p class="description fade-in-up delay-2">基于Android深度定制，为全球用户打造流畅、智能、个性化的操作系统</p>
          <div class="scroll-indicator fade-in-up delay-3">
            <div class="scroll-arrow"></div>
          </div>
        </div>
      </div>
      <div class="hero-decoration"></div>
      <div class="hero-decoration-2"></div>
    </section>

    <!-- Features Section -->
    <section class="features" ref="featuresSection">
      <div class="container">
        <h2 class="section-title" :class="{ 'animate-in': featuresVisible }">核心特性</h2>
        <div class="features-grid">
          <div
            class="feature-card"
            v-for="(feature, index) in features"
            :key="feature.title"
            :class="{ 'animate-in': featuresVisible }"
            :style="{ animationDelay: `${index * 0.1}s` }"
          >
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3 class="feature-title">{{ feature.title }}</h3>
            <p class="feature-desc">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Design Section -->
    <section class="design" ref="designSection">
      <div class="container">
        <h2 class="section-title" :class="{ 'animate-in': designVisible }">设计理念</h2>
        <div class="design-content">
          <div
            class="design-item"
            v-for="(item, index) in designPrinciples"
            :key="item.title"
            :class="{ 'animate-in': designVisible }"
            :style="{ animationDelay: `${index * 0.15}s` }"
          >
            <h3 class="design-title">{{ item.title }}</h3>
            <p class="design-desc">{{ item.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Technology Section -->
    <section class="technology" ref="techSection">
      <div class="container">
        <h2 class="section-title" :class="{ 'animate-in': techVisible }">技术创新</h2>
        <div class="tech-grid">
          <div
            class="tech-card"
            v-for="(tech, index) in technologies"
            :key="tech.name"
            :class="{ 'animate-in': techVisible }"
            :style="{ animationDelay: `${index * 0.1}s` }"
          >
            <div class="tech-badge">{{ tech.badge }}</div>
            <h3 class="tech-name">{{ tech.name }}</h3>
            <p class="tech-detail">{{ tech.detail }}</p>
            <div class="tech-glow"></div>
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
import { ref, onMounted } from 'vue'

// Intersection Observer for scroll animations
const featuresSection = ref(null)
const designSection = ref(null)
const techSection = ref(null)
const featuresVisible = ref(false)
const designVisible = ref(false)
const techVisible = ref(false)

onMounted(() => {
  const observerOptions = {
    threshold: 0.2,
    rootMargin: '0px 0px -100px 0px'
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        if (entry.target === featuresSection.value) {
          featuresVisible.value = true
        } else if (entry.target === designSection.value) {
          designVisible.value = true
        } else if (entry.target === techSection.value) {
          techVisible.value = true
        }
      }
    })
  }, observerOptions)

  if (featuresSection.value) observer.observe(featuresSection.value)
  if (designSection.value) observer.observe(designSection.value)
  if (techSection.value) observer.observe(techSection.value)
})

// Particle animation styles
const getParticleStyle = (index) => {
  const size = Math.random() * 4 + 2
  const duration = Math.random() * 20 + 10
  const delay = Math.random() * 5
  const xPos = Math.random() * 100
  const opacity = Math.random() * 0.5 + 0.1

  return {
    width: `${size}px`,
    height: `${size}px`,
    left: `${xPos}%`,
    animationDuration: `${duration}s`,
    animationDelay: `${delay}s`,
    opacity: opacity
  }
}

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
  position: relative;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

/* Floating Particles */
.particles {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
  overflow: hidden;
}

.particle {
  position: absolute;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.8) 0%, rgba(255, 255, 255, 0.2) 100%);
  border-radius: 50%;
  animation: float linear infinite;
  bottom: -10px;
}

@keyframes float {
  0% {
    transform: translateY(0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    transform: translateY(-100vh) rotate(360deg);
    opacity: 0;
  }
}

/* Fade In Up Animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in-up {
  animation: fadeInUp 1s ease-out forwards;
  opacity: 0;
}

.delay-1 {
  animation-delay: 0.2s;
}

.delay-2 {
  animation-delay: 0.4s;
}

.delay-3 {
  animation-delay: 0.6s;
}

/* Scroll Indicator */
.scroll-indicator {
  margin-top: 3rem;
  display: flex;
  justify-content: center;
}

.scroll-arrow {
  width: 30px;
  height: 50px;
  border: 2px solid rgba(255, 255, 255, 0.5);
  border-radius: 25px;
  position: relative;
  animation: scroll-bounce 2s infinite;
}

.scroll-arrow::before {
  content: '';
  position: absolute;
  top: 8px;
  left: 50%;
  width: 6px;
  height: 6px;
  background: rgba(255, 255, 255, 0.8);
  border-radius: 50%;
  transform: translateX(-50%);
  animation: scroll-move 2s infinite;
}

@keyframes scroll-bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(10px);
  }
}

@keyframes scroll-move {
  0% {
    opacity: 1;
    transform: translate(-50%, 0);
  }
  100% {
    opacity: 0;
    transform: translate(-50%, 20px);
  }
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
  background: radial-gradient(circle,
    rgba(255, 107, 107, 0.15) 0%,
    rgba(254, 202, 87, 0.1) 25%,
    rgba(72, 219, 251, 0.1) 50%,
    rgba(255, 159, 243, 0.1) 75%,
    transparent 70%);
  border-radius: 50%;
  animation: pulse 4s ease-in-out infinite;
}

.hero-decoration-2 {
  position: absolute;
  top: 20%;
  right: 10%;
  width: 400px;
  height: 400px;
  background: radial-gradient(circle,
    rgba(139, 92, 246, 0.1) 0%,
    rgba(59, 130, 246, 0.05) 50%,
    transparent 70%);
  border-radius: 50%;
  animation: pulse-reverse 6s ease-in-out infinite;
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

@keyframes pulse-reverse {
  0%, 100% {
    transform: scale(1.1);
    opacity: 0.3;
  }
  50% {
    transform: scale(1);
    opacity: 0.6;
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
  background: linear-gradient(135deg, #ff6b6b 0%, #feca57 20%, #48dbfb 40%, #ff9ff3 60%, #54a0ff 80%, #5f27cd 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -0.02em;
  animation: gradient-shift 8s ease infinite;
  background-size: 200% auto;
}

@keyframes gradient-shift {
  0%, 100% {
    background-position: 0% center;
  }
  50% {
    background-position: 100% center;
  }
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
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.6s ease;
}

.section-title.animate-in {
  opacity: 1;
  transform: translateY(0);
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
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  opacity: 0;
  transform: translateY(30px);
}

.feature-card.animate-in {
  animation: slideInUp 0.6s ease-out forwards;
}

@keyframes slideInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.feature-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(255, 255, 255, 0.2);
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  display: inline-block;
  transition: transform 0.3s ease;
  filter: drop-shadow(0 0 10px rgba(255, 255, 255, 0.3));
}

.feature-card:hover .feature-icon {
  transform: scale(1.2) rotate(5deg);
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
  transition: all 0.4s ease;
  opacity: 0;
  transform: translateX(-30px);
}

.design-item.animate-in {
  animation: slideInRight 0.6s ease-out forwards;
}

@keyframes slideInRight {
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.design-item:hover {
  border-left-color: #ffffff;
  transform: translateX(10px);
  padding-left: 2.5rem;
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
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  opacity: 0;
  transform: scale(0.9);
}

.tech-card.animate-in {
  animation: scaleIn 0.6s ease-out forwards;
}

@keyframes scaleIn {
  to {
    opacity: 1;
    transform: scale(1);
  }
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
  transform-origin: left;
  transition: transform 0.5s ease;
}

.tech-card:hover::before {
  transform: scaleX(1);
}

.tech-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(139, 92, 246, 0.2) 0%, transparent 70%);
  transform: translate(-50%, -50%) scale(0);
  transition: transform 0.5s ease;
  pointer-events: none;
}

.tech-card:hover {
  transform: translateY(-8px) scale(1.02);
  border-color: rgba(255, 255, 255, 0.3);
  box-shadow: 0 20px 40px rgba(139, 92, 246, 0.3);
}

.tech-card:hover .tech-glow {
  transform: translate(-50%, -50%) scale(1.5);
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

