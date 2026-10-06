<script setup>
const stats = [
  { num: '2', unit: '分钟', label: '每次刷牙时长' },
  { num: '2', unit: '次', label: '每天刷牙次数' },
  { num: '1', unit: '次', label: '每天牙线清洁' },
  { num: '6~12', unit: '月', label: '建议口腔检查间隔' }
]
</script>

<template>
  <section class="hero" id="top">
    <div class="hero__glow hero__glow--a"></div>
    <div class="hero__glow hero__glow--b"></div>
    <div class="hero__inner">
      <p class="hero__tag">科学护牙 · 从选对工具开始</p>
      <h1 class="hero__title">
        你的口腔<br />
        <span>值得被认真对待</span>
      </h1>
      <p class="hero__sub">
        牙刷只能清洁约 60% 的牙面，剩下的死角需要不同工具配合。
        这份科普帮你搞懂：什么时候该用什么工具、怎么用、以及常见误区。
      </p>
      <a class="hero__cta" href="#tools">查看护理工具大全 →</a>

      <div class="hero__stats">
        <div v-for="s in stats" :key="s.label" class="stat">
          <div class="stat__num">{{ s.num }}<small>{{ s.unit }}</small></div>
          <div class="stat__label">{{ s.label }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  overflow: hidden;
  padding: 72px 20px 64px;
  background: linear-gradient(160deg, #eef7ff 0%, #f4fbff 45%, #ffffff 100%);
}
.hero__glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(70px);
  opacity: 0.55;
  pointer-events: none;
}
.hero__glow--a {
  width: 340px;
  height: 340px;
  background: #7ec8ff;
  top: -120px;
  right: -60px;
}
.hero__glow--b {
  width: 300px;
  height: 300px;
  background: #b6f0d8;
  bottom: -140px;
  left: -80px;
}
.hero__inner {
  position: relative;
  max-width: 880px;
  margin: 0 auto;
  text-align: center;
}
.hero__tag {
  display: inline-block;
  font-size: 0.85rem;
  color: var(--brand);
  background: #fff;
  border: 1px solid var(--line);
  padding: 6px 16px;
  border-radius: 999px;
  box-shadow: 0 4px 14px rgba(28, 120, 200, 0.08);
  margin: 0 0 22px;
}
.hero__title {
  font-size: clamp(2.1rem, 6vw, 3.6rem);
  line-height: 1.15;
  margin: 0 0 20px;
  color: var(--text-1);
  letter-spacing: -0.02em;
}
.hero__title span {
  background: linear-gradient(100deg, #1f8fe0, #22b58a);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
.hero__sub {
  max-width: 620px;
  margin: 0 auto 28px;
  color: var(--text-2);
  font-size: 1.02rem;
  line-height: 1.85;
}
.hero__cta {
  display: inline-block;
  background: var(--brand);
  color: #fff;
  text-decoration: none;
  font-weight: 600;
  padding: 13px 30px;
  border-radius: 999px;
  box-shadow: 0 10px 24px rgba(31, 143, 224, 0.32);
  transition: 0.2s;
}
.hero__cta:hover {
  transform: translateY(-2px);
  box-shadow: 0 14px 30px rgba(31, 143, 224, 0.42);
}
.hero__stats {
  margin-top: 52px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 14px;
}
.stat {
  background: rgba(255, 255, 255, 0.8);
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 18px 10px;
}
.stat__num {
  font-size: 1.75rem;
  font-weight: 700;
  color: var(--brand);
}
.stat__num small {
  font-size: 0.85rem;
  font-weight: 600;
  margin-left: 2px;
}
.stat__label {
  font-size: 0.82rem;
  color: var(--text-2);
  margin-top: 4px;
}
@media (max-width: 640px) {
  .hero { padding: 52px 16px 48px; }
  .hero__stats { grid-template-columns: repeat(2, 1fr); }
}
</style>
