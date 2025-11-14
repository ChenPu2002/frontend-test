<template>
  <div class="app">
    <header class="site-header" :class="{ 'is-scrolled': isScrolled, 'nav-open': isNavOpen }">
      <div class="container header-inner">
        <a class="logo" href="#home" @click="handleNavLink">ColorOS</a>
        <nav class="nav">
          <a v-for="link in navLinks" :key="link.label" :href="link.href" @click="handleNavLink">
            {{ link.label }}
          </a>
        </nav>
        <div class="header-actions">
          <button class="ghost-btn">开发者中心</button>
          <button class="solid-btn">立即下载</button>
        </div>
        <button class="mobile-trigger" @click="toggleNav" aria-label="切换导航">
          <span></span>
          <span></span>
        </button>
      </div>
    </header>

    <main>
      <section class="hero" id="home">
        <div class="hero-background"></div>
        <div class="container hero-grid">
          <div class="hero-content">
            <p class="eyebrow">ColorOS 14 · Aquamorphic Design 2.0</p>
            <h1>无边界的智能体验</h1>
            <p class="lead">
              以水之灵感打造全新流体秩序，ColorOS 通过跨端算力、AI 能力与多设备生态，塑造更沉浸、更可信赖的日常体验。
            </p>
            <div class="hero-actions">
              <button class="solid-btn large">探索 ColorOS 14</button>
              <button class="ghost-btn large">观看发布会</button>
            </div>
            <div class="hero-metrics">
              <div class="metric" v-for="metric in heroMetrics" :key="metric.label">
                <span class="value">{{ metric.value }}</span>
                <span class="label">{{ metric.label }}</span>
              </div>
            </div>
          </div>

          <div class="hero-visual">
            <div class="floating-chip">
              <span>Fluid Cloud</span>
              <p>随场景自适应的通知体验</p>
            </div>
            <div class="phone-frame">
              <div class="screen">
                <div class="screen-gradient"></div>
                <div class="screen-content">
                  <span class="chip">Pantanal</span>
                  <h3>跨端智慧流转</h3>
                  <p>文件、通话、任务在任意设备间自然流动。</p>
                  <div class="screen-pill">
                    <span>ColorOS 14</span>
                    <svg viewBox="0 0 16 16" aria-hidden="true">
                      <path
                        d="M5 3l6 5-6 5"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="1.5"
                        stroke-linecap="round"
                        stroke-linejoin="round"
                      />
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="experience-section" id="features">
        <div class="container section-header">
          <p class="eyebrow">体验升级</p>
          <h2>轻盈、灵动、智能的全局体验</h2>
          <p>
            ColorOS 将系统级动画、效率与安全体验合而为一，让每一次触控都顺畅、每一次协作都高效。
          </p>
        </div>
        <div class="container experience-grid">
          <article
            class="experience-card"
            v-for="card in experienceCards"
            :key="card.title"
            :class="`theme-${card.theme}`"
          >
            <div class="card-tag">{{ card.tag }}</div>
            <h3>{{ card.title }}</h3>
            <p>{{ card.description }}</p>
            <button class="text-link">
              了解详情
              <svg viewBox="0 0 16 16" aria-hidden="true">
                <path
                  d="M4 8h8M8 4l4 4-4 4"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </button>
          </article>
        </div>
      </section>

      <section class="highlight-panel" id="design">
        <div class="container highlight-grid">
          <div class="panel-hero">
            <p class="eyebrow">ColorOS 14 视觉语言</p>
            <h2>水之灵感，流动在每一次呼吸间</h2>
            <p>
              Aquamorphic Design 2.0 以自然的水体为灵感，构建兼具秩序与情感的视觉体系：流体光影、柔和质感以及留白的平衡，共同塑造轻盈而沉浸的使用体验。
            </p>
            <div class="panel-video">
              <div class="video-glow"></div>
              <div class="video-caption">
                <span>概念短片</span>
                <strong>ColorOS Visual Studio</strong>
              </div>
            </div>
          </div>
          <div class="highlight-list">
            <article class="highlight-item" v-for="item in highlights" :key="item.title">
              <span class="badge">{{ item.badge }}</span>
              <h3>{{ item.title }}</h3>
              <p>{{ item.copy }}</p>
            </article>
          </div>
        </div>
      </section>

      <section class="ecosystem" id="devices">
        <div class="container section-header">
          <p class="eyebrow">生态互联</p>
          <h2>多设备协同，真正的无界流转</h2>
          <p>
            支持手机、折叠屏、平板、手表、耳机与 IoT 合作伙伴的无缝协作，让内容与服务在不同屏幕持续流动。
          </p>
        </div>
        <div class="device-track">
          <article
            class="device-card"
            v-for="device in ecosystemDevices"
            :key="device.name"
            :style="{ '--card-color': device.color, '--card-accent': device.accent }"
          >
            <div class="device-label">{{ device.category }}</div>
            <h3>{{ device.name }}</h3>
            <p>{{ device.description }}</p>
            <div class="device-illustration">
              <span>ColorOS Inside</span>
            </div>
          </article>
        </div>
      </section>

      <section class="design-lab" id="vision">
        <div class="container design-layout">
          <div class="design-intro">
            <p class="eyebrow">设计愿景</p>
            <h2>无边界设计实验室</h2>
            <p>
              ColorOS Design Lab 与全球艺术家、声音设计师及交互专家合作，从视觉、听觉到触感共创“温度科技”。通过与自然共鸣的材质、颜色与动效，赋予系统鲜活生命力。
            </p>
            <button class="ghost-btn">了解设计故事</button>
          </div>
          <div class="design-pillars">
            <article class="pillar" v-for="pillar in designPillars" :key="pillar.title">
              <h3>{{ pillar.title }}</h3>
              <p>{{ pillar.description }}</p>
            </article>
          </div>
        </div>
      </section>

      <section class="timeline" id="timeline">
        <div class="container">
          <div class="section-header compact">
            <p class="eyebrow">发展历程</p>
            <h2>十余年持续进化</h2>
          </div>
          <div class="timeline-track">
            <article class="timeline-item" v-for="node in timeline" :key="node.year">
              <span class="year">{{ node.year }}</span>
              <h3>{{ node.title }}</h3>
              <p>{{ node.detail }}</p>
            </article>
          </div>
        </div>
      </section>

      <section class="labs" id="labs">
        <div class="container section-header compact">
          <p class="eyebrow">ColorOS Labs</p>
          <h2>与开发者共创未来</h2>
        </div>
        <div class="container labs-grid">
          <article class="lab-card" v-for="lab in labs" :key="lab.title">
            <div class="lab-tag">{{ lab.tag }}</div>
            <h3>{{ lab.title }}</h3>
            <p>{{ lab.description }}</p>
            <button class="text-link">
              {{ lab.link }}
              <svg viewBox="0 0 16 16" aria-hidden="true">
                <path
                  d="M4 8h8M8 4l4 4-4 4"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </button>
          </article>
        </div>
      </section>

      <section class="cta" id="download">
        <div class="container cta-card">
          <div>
            <p class="eyebrow">ColorOS 公测计划</p>
            <h2>第一时间体验最新版本</h2>
            <p>加入 Beta 计划，抢先体验全新能力，并为 ColorOS 的进化提供宝贵建议。</p>
          </div>
          <div class="cta-actions">
            <button class="solid-btn large">下载公测包</button>
            <button class="ghost-btn large">查看升级计划</button>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="container footer-grid">
        <div class="footer-brand">
          <span>ColorOS</span>
          <p>让科技更有温度 · OPPO 官方操作系统</p>
        </div>
        <div class="footer-links" v-for="group in footerLinks" :key="group.title">
          <h4>{{ group.title }}</h4>
          <a v-for="item in group.items" :key="item" href="#">{{ item }}</a>
        </div>
      </div>
      <div class="footer-bottom">
        <span>© 2025 OPPO. All Rights Reserved.</span>
        <a href="#">隐私政策</a>
        <a href="#">联系我们</a>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue'

const navLinks = [
  { label: '首页', href: '#home' },
  { label: '体验', href: '#features' },
  { label: '设计', href: '#design' },
  { label: '生态', href: '#devices' },
  { label: '愿景', href: '#vision' },
  { label: '升级', href: '#timeline' }
]

const heroMetrics = [
  { value: '6.5亿+', label: '全球用户' },
  { value: '3000+', label: '生态伙伴' },
  { value: '54万+', label: '开发者' }
]

const experienceCards = [
  {
    title: '流体云',
    description: '系统通知进化为可交互的立体颗粒，追随任务在屏幕上自然浮现，随时可拖拽至其他设备继续。',
    tag: 'ColorOS 14',
    theme: 'cyan'
  },
  {
    title: 'Aquamorphic 2.0',
    description: '受水启发的视觉系统带来柔和光影、空间留白与声景设计，营造舒缓、沉浸的观感与听感。',
    tag: '设计语言',
    theme: 'blue'
  },
  {
    title: 'Trinity 引擎',
    description: '算力、内存、存储三重调度引擎，分配更聪明，重载依旧丝滑，久用也如新机。',
    tag: '性能',
    theme: 'purple'
  },
  {
    title: '小布助手',
    description: '语音、图像与跨端知识库全面升级，AI 能力贯穿生活与工作，主动提供更贴心建议。',
    tag: 'AI',
    theme: 'orange'
  }
]

const highlights = [
  {
    badge: 'Pantanal',
    title: '跨端智慧流转',
    copy: '文件、通话、任务在手机、平板、电脑之间无缝衔接，不同设备共享一套体验。'
  },
  {
    badge: '安全岛',
    title: '全链路隐私防护',
    copy: 'TEE + 隐私沙盒双重防护，敏感权限可视可控，数据安全一眼尽览。'
  },
  {
    badge: '超算平台',
    title: '云端算力协同',
    copy: '端侧性能与云端算力实时协作，图形渲染、翻译、AI 创作都有超级动力。'
  },
  {
    badge: '万能互联',
    title: '生态接入无门槛',
    copy: '广泛兼容第三方硬件，NFC 触碰即连，跨品牌亦可享受一致体验。'
  }
]

const ecosystemDevices = [
  {
    name: 'Find X7 Ultra',
    category: '影像旗舰',
    description: '双潜望四摄 + HyperTone 影像系统，旗舰体验与 ColorOS 深度融合。',
    color: '#fdf1ec',
    accent: '#ff8f5c'
  },
  {
    name: 'Find N3',
    category: '折叠旗舰',
    description: '轻薄大屏与竖屏交互，折叠状态下依然畅享 ColorOS 的多任务体验。',
    color: '#edf4ff',
    accent: '#5c7cfa'
  },
  {
    name: 'OPPO Pad 3',
    category: '生产力平板',
    description: '兼容分屏与跨屏协同，键鼠共享、一拉即合，办公更高效。',
    color: '#eefaf6',
    accent: '#16c2a3'
  },
  {
    name: 'OPPO Watch X',
    category: '健康穿戴',
    description: '全场景健康守护，来电、导航与提醒均可在流体云中继续。',
    color: '#f4f0ff',
    accent: '#8c6bff'
  }
]

const designPillars = [
  {
    title: '轻盈秩序',
    description: '通过留白与层级营造清爽空间，信息传递更聚焦，视觉节奏更舒适。'
  },
  {
    title: '灵动交互',
    description: '流体动画遵循真实物理规律，让每一次滑动、拖拽都拥有自然反馈。'
  },
  {
    title: '温暖科技',
    description: '声音、触感与动画协同表达情感温度，让科技更有人性。'
  }
]

const timeline = [
  { year: '2013', title: 'ColorOS 1.0', detail: '首发即搭载个性主题与图标，开启 ColorOS 的设计探索。' },
  { year: '2019', title: 'ColorOS 7', detail: '引入无边界设计理念，轻盈视觉与多端协同迈出第一步。' },
  { year: '2021', title: 'ColorOS 12', detail: 'Aquamorphic Design 雏形诞生，国际化体验全面升级。' },
  { year: '2023', title: 'ColorOS 14', detail: 'Fluid Cloud、Trinity 引擎与 Pantanal 系统正式亮相。' }
]

const labs = [
  {
    tag: '开发者',
    title: 'Pantanal 跨端系统',
    description: '一次开发覆盖多设备，原子化服务随处可用，轻松接入 ColorOS 生态。',
    link: '查看文档'
  },
  {
    tag: 'AI 能力',
    title: '小布开放平台',
    description: '调用语音、图像理解与大模型能力，为应用带来更聪明的交互。',
    link: '申请接入'
  },
  {
    tag: '体验计划',
    title: 'ColorOS Beta 社区',
    description: '抢先试用实验功能，与工程师直接交流，共建更好的系统体验。',
    link: '加入社区'
  }
]

const footerLinks = [
  { title: '产品', items: ['ColorOS 14', 'ColorOS 13', '升级计划', '流体云体验'] },
  { title: '服务', items: ['开发者中心', '开放平台', '安全响应', 'ColorOS 社区'] },
  { title: '支持', items: ['隐私政策', 'OPPO 官网', '售后支持', '联系我们'] }
]

const isScrolled = ref(false)
const isNavOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 24
}

const toggleNav = () => {
  isNavOpen.value = !isNavOpen.value
}

const handleNavLink = () => {
  isNavOpen.value = false
}

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll)
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.app {
  background: linear-gradient(180deg, #f7f9fb 0%, #ffffff 35%, #f5f8ff 70%, #fefefe 100%);
  color: #0b0b0f;
  min-height: 100vh;
}

.container {
  width: min(1200px, 90vw);
  margin: 0 auto;
}

.eyebrow {
  font-size: 0.9rem;
  letter-spacing: 0.24em;
  text-transform: uppercase;
  color: #0eb7ff;
  margin-bottom: 0.75rem;
}

.site-header {
  position: sticky;
  top: 0;
  z-index: 10;
  padding: 1.25rem 0;
  transition: all 0.3s ease;
}

.site-header::after {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(255, 255, 255, 0.75);
  box-shadow: 0 10px 40px rgba(15, 23, 42, 0.08);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s ease;
}

.site-header.is-scrolled::after {
  opacity: 1;
  backdrop-filter: blur(12px);
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
  position: relative;
  z-index: 1;
}

.logo {
  font-size: 1.25rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.nav {
  display: flex;
  gap: 1.5rem;
  font-size: 0.95rem;
  color: rgba(15, 23, 42, 0.8);
}

.nav a {
  position: relative;
  padding-bottom: 0.25rem;
}

.nav a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, #00f0ff, #0061ff);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.nav a:hover::after {
  transform: scaleX(1);
}

.header-actions {
  display: flex;
  gap: 0.75rem;
  align-items: center;
}

.ghost-btn,
.solid-btn {
  border-radius: 999px;
  padding: 0.6rem 1.6rem;
  font-size: 0.95rem;
  font-weight: 600;
  transition: all 0.3s ease;
  border: 1px solid transparent;
  background: transparent;
  color: #0b0b0f;
}

.solid-btn {
  background: linear-gradient(120deg, #00f0ff 0%, #0084ff 100%);
  color: #051327;
  border: none;
  box-shadow: 0 12px 30px rgba(0, 132, 255, 0.26);
}

.solid-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 18px 40px rgba(0, 132, 255, 0.35);
}

.ghost-btn {
  border-color: rgba(5, 19, 39, 0.15);
  color: #051327;
}

.ghost-btn:hover {
  border-color: rgba(5, 19, 39, 0.4);
}

.solid-btn.large,
.ghost-btn.large {
  padding: 0.85rem 2.4rem;
  font-size: 1rem;
}

.mobile-trigger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  padding: 0;
}

.mobile-trigger span {
  width: 24px;
  height: 2px;
  background: #0b0b0f;
  transition: transform 0.3s ease;
}

.hero {
  position: relative;
  padding: 8rem 0 6rem;
  overflow: hidden;
}

.hero-background {
  position: absolute;
  inset: 10% 5% auto;
  height: 90%;
  background: radial-gradient(circle at 20% 20%, rgba(0, 240, 255, 0.35), transparent 50%),
    radial-gradient(circle at 80% 30%, rgba(0, 111, 255, 0.3), transparent 45%),
    radial-gradient(circle at 50% 80%, rgba(255, 255, 255, 0.8), transparent 60%);
  filter: blur(50px);
  opacity: 0.8;
}

.hero-grid {
  position: relative;
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  align-items: center;
  gap: 4rem;
}

.hero-content h1 {
  font-size: clamp(2.8rem, 4vw, 4rem);
  line-height: 1.1;
  margin-bottom: 1rem;
  color: #020617;
}

.lead {
  font-size: 1.1rem;
  color: rgba(2, 6, 23, 0.8);
  max-width: 540px;
  line-height: 1.8;
  margin-bottom: 2rem;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 2.5rem;
}

.hero-metrics {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.5rem;
}

.metric {
  padding-left: 1rem;
  border-left: 2px solid rgba(2, 6, 23, 0.15);
}

.metric .value {
  display: block;
  font-size: 1.75rem;
  font-weight: 600;
  color: #020617;
}

.metric .label {
  color: rgba(2, 6, 23, 0.6);
  font-size: 0.95rem;
}

.hero-visual {
  position: relative;
  display: flex;
  justify-content: center;
}

.floating-chip {
  position: absolute;
  top: -1rem;
  right: 2rem;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 16px;
  padding: 0.75rem 1.25rem;
  box-shadow: 0 15px 35px rgba(15, 23, 42, 0.12);
}

.floating-chip span {
  font-weight: 600;
  color: #0084ff;
}

.floating-chip p {
  font-size: 0.85rem;
  color: rgba(15, 23, 42, 0.75);
}

.phone-frame {
  width: 320px;
  border-radius: 36px;
  padding: 0.8rem;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.8), rgba(211, 219, 236, 0.8));
  box-shadow: 0 35px 70px rgba(15, 23, 42, 0.18);
}

.screen {
  border-radius: 28px;
  position: relative;
  overflow: hidden;
  height: 540px;
  background: #020617;
}

.screen-gradient {
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at 30% 20%, rgba(0, 240, 255, 0.6), transparent),
    radial-gradient(circle at 80% 20%, rgba(0, 102, 255, 0.5), transparent),
    radial-gradient(circle at 50% 80%, rgba(255, 255, 255, 0.2), transparent);
  animation: orbit 8s linear infinite;
}

@keyframes orbit {
  0% {
    transform: translate3d(0, 0, 0);
  }

  50% {
    transform: translate3d(-10px, 10px, 0);
  }

  100% {
    transform: translate3d(0, 0, 0);
  }
}

.screen-content {
  position: relative;
  padding: 2.5rem 2rem;
  color: #e2f7ff;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.screen-content h3 {
  font-size: 1.5rem;
}

.screen-content p {
  color: rgba(226, 247, 255, 0.8);
  line-height: 1.6;
}

.chip {
  align-self: flex-start;
  padding: 0.4rem 1rem;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.12);
  font-size: 0.85rem;
}

.screen-pill {
  margin-top: 1rem;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.6rem 1.2rem;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.15);
}

.screen-pill svg {
  width: 16px;
  height: 16px;
}

.section-header {
  text-align: center;
  margin-bottom: 3.5rem;
}

.section-header h2 {
  font-size: clamp(2rem, 3.2vw, 3rem);
  margin-bottom: 1rem;
  color: #020617;
}

.section-header p {
  max-width: 680px;
  margin: 0 auto;
  color: rgba(2, 6, 23, 0.7);
  line-height: 1.8;
}

.experience-section {
  padding: 6rem 0 4rem;
}

.experience-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.5rem;
}

.experience-card {
  border-radius: 24px;
  padding: 2.25rem;
  background: #ffffff;
  min-height: 260px;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  box-shadow: 0 30px 60px rgba(15, 23, 42, 0.08);
  border: 1px solid rgba(15, 23, 42, 0.05);
}

.experience-card h3 {
  font-size: 1.4rem;
  color: #020617;
}

.experience-card p {
  color: rgba(2, 6, 23, 0.65);
  line-height: 1.7;
}

.card-tag {
  font-size: 0.85rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.text-link {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  font-weight: 600;
  background: none;
  border: none;
  color: inherit;
  padding: 0;
}

.text-link svg {
  width: 16px;
  height: 16px;
}

.experience-card.theme-cyan {
  background: linear-gradient(180deg, #f2ffff, #ffffff);
  border-color: rgba(0, 240, 255, 0.3);
}

.experience-card.theme-blue {
  background: linear-gradient(180deg, #f2f6ff, #ffffff);
  border-color: rgba(0, 102, 255, 0.25);
}

.experience-card.theme-purple {
  background: linear-gradient(180deg, #f6f4ff, #ffffff);
  border-color: rgba(119, 67, 255, 0.25);
}

.experience-card.theme-orange {
  background: linear-gradient(180deg, #fff6f0, #ffffff);
  border-color: rgba(255, 149, 0, 0.25);
}

.highlight-panel {
  padding: 5rem 0;
}

.highlight-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2.5rem;
  align-items: start;
}

.panel-hero {
  background: #030712;
  color: #e0f2ff;
  border-radius: 32px;
  padding: 3rem;
  position: relative;
  overflow: hidden;
  min-height: 480px;
}

.panel-hero::after {
  content: '';
  position: absolute;
  top: -30%;
  right: -20%;
  width: 65%;
  height: 65%;
  background: radial-gradient(circle, rgba(0, 240, 255, 0.5), transparent 60%);
  filter: blur(30px);
}

.panel-hero h2 {
  color: #fff;
}

.panel-video {
  margin-top: 2rem;
  border-radius: 24px;
  background: radial-gradient(circle at 20% 20%, rgba(0, 240, 255, 0.3), transparent),
    radial-gradient(circle at 80% 60%, rgba(0, 102, 255, 0.35), transparent);
  min-height: 180px;
  position: relative;
  overflow: hidden;
}

.video-glow {
  position: absolute;
  inset: 0;
  background: linear-gradient(120deg, rgba(255, 255, 255, 0.1), transparent);
  animation: shimmer 4s linear infinite;
}

@keyframes shimmer {
  0% {
    transform: translateX(-100%);
  }

  100% {
    transform: translateX(100%);
  }
}

.video-caption {
  position: absolute;
  bottom: 1.25rem;
  left: 1.5rem;
}

.highlight-list {
  display: grid;
  gap: 1rem;
}

.highlight-item {
  padding: 1.75rem;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.6);
  border: 1px solid rgba(15, 23, 42, 0.08);
  box-shadow: 0 20px 45px rgba(15, 23, 42, 0.08);
}

.highlight-item h3 {
  margin: 0.5rem 0;
  color: #020617;
}

.highlight-item p {
  color: rgba(2, 6, 23, 0.7);
  line-height: 1.6;
}

.badge {
  display: inline-block;
  padding: 0.35rem 1rem;
  border-radius: 999px;
  background: rgba(0, 113, 255, 0.1);
  color: #0050ff;
  font-size: 0.85rem;
  font-weight: 600;
}

.ecosystem {
  padding: 5rem 0;
}

.device-track {
  display: flex;
  gap: 1.5rem;
  overflow-x: auto;
  padding: 0 5vw 0 5vw;
  scroll-snap-type: x mandatory;
}

.device-card {
  flex: 0 0 260px;
  border-radius: 32px;
  padding: 2rem;
  background: var(--card-color, #ffffff);
  scroll-snap-align: start;
  position: relative;
  box-shadow: 0 30px 60px rgba(15, 23, 42, 0.08);
  border: 1px solid rgba(15, 23, 42, 0.05);
}

.device-label {
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: rgba(15, 23, 42, 0.5);
}

.device-card h3 {
  margin: 1rem 0 0.5rem;
}

.device-illustration {
  margin-top: 2rem;
  border-radius: 24px;
  padding: 2rem;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.8), transparent);
  border: 1px dashed rgba(15, 23, 42, 0.1);
  text-align: center;
  color: var(--card-accent, #0f172a);
  font-weight: 600;
}

.design-lab {
  padding: 6rem 0;
}

.design-layout {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2.5rem;
  align-items: start;
}

.design-intro {
  background: rgba(255, 255, 255, 0.9);
  border-radius: 32px;
  padding: 3rem;
  box-shadow: 0 30px 70px rgba(15, 23, 42, 0.08);
}

.design-intro p {
  color: rgba(2, 6, 23, 0.8);
  margin-bottom: 2rem;
  line-height: 1.8;
}

.design-pillars {
  display: grid;
  gap: 1rem;
}

.pillar {
  padding: 1.75rem;
  border-radius: 24px;
  background: #ffffff;
  border: 1px solid rgba(15, 23, 42, 0.08);
  box-shadow: 0 25px 50px rgba(15, 23, 42, 0.05);
}

.pillar h3 {
  margin-bottom: 0.5rem;
}

.timeline {
  padding: 5rem 0;
  background: radial-gradient(circle at top, rgba(0, 240, 255, 0.15), transparent 55%);
}

.timeline-track {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
}

.timeline-item {
  padding: 2rem;
  border-radius: 24px;
  background: #ffffff;
  border: 1px solid rgba(15, 23, 42, 0.08);
  position: relative;
}

.timeline-item::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 24px;
  padding: 1px;
  background: linear-gradient(120deg, rgba(0, 240, 255, 0.6), rgba(0, 102, 255, 0.4));
  mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
}

.timeline-item .year {
  display: inline-flex;
  padding: 0.35rem 1rem;
  border-radius: 999px;
  background: rgba(0, 102, 255, 0.08);
  color: #004dff;
  font-weight: 600;
}

.timeline-item h3 {
  margin: 1rem 0 0.5rem;
}

.labs {
  padding: 5rem 0;
}

.labs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.5rem;
}

.lab-card {
  padding: 2rem;
  border-radius: 28px;
  background: linear-gradient(180deg, rgba(0, 240, 255, 0.12), rgba(255, 255, 255, 0.9));
  border: 1px solid rgba(0, 102, 255, 0.2);
  box-shadow: 0 30px 60px rgba(15, 23, 42, 0.08);
}

.lab-tag {
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: rgba(2, 6, 23, 0.6);
}

.cta {
  padding: 5rem 0 6rem;
}

.cta-card {
  border-radius: 40px;
  padding: 3rem;
  background: linear-gradient(120deg, rgba(0, 240, 255, 0.25), rgba(0, 102, 255, 0.35), rgba(255, 255, 255, 0.85));
  display: flex;
  justify-content: space-between;
  gap: 2rem;
  flex-wrap: wrap;
  color: #030712;
}

.cta-card p {
  max-width: 480px;
}

.cta-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  align-items: center;
}

.footer {
  padding: 4rem 0 2rem;
  background: #020617;
  color: rgba(226, 232, 255, 0.8);
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 2rem;
  margin-bottom: 2rem;
}

.footer-brand span {
  font-size: 1.4rem;
  font-weight: 600;
  color: #fff;
}

.footer-links h4 {
  color: #fff;
  margin-bottom: 0.75rem;
}

.footer-links a {
  display: block;
  color: inherit;
  margin-bottom: 0.4rem;
  font-size: 0.95rem;
}

.footer-bottom {
  border-top: 1px solid rgba(148, 163, 184, 0.2);
  padding-top: 1.5rem;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  font-size: 0.9rem;
}

.footer-bottom a {
  color: rgba(226, 232, 255, 0.9);
}

@media (max-width: 1024px) {
  .nav {
    position: absolute;
    inset: 100% 0 auto;
    background: rgba(255, 255, 255, 0.95);
    padding: 1rem 2rem;
    flex-direction: column;
    transform-origin: top;
    transform: scaleY(0);
    opacity: 0;
    pointer-events: none;
    box-shadow: 0 20px 40px rgba(15, 23, 42, 0.12);
  }

  .site-header.nav-open .nav {
    transform: scaleY(1);
    opacity: 1;
    pointer-events: auto;
  }

  .mobile-trigger {
    display: flex;
  }

  .header-actions {
    display: none;
  }

  .hero-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 768px) {
  .hero {
    padding-top: 6rem;
  }

  .hero-metrics {
    grid-template-columns: 1fr;
  }

  .experience-grid {
    grid-template-columns: 1fr;
  }

  .highlight-grid {
    grid-template-columns: 1fr;
  }

  .device-track {
    padding-inline: 1.5rem;
  }

  .cta-card {
    padding: 2.25rem;
  }
}
</style>

