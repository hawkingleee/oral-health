<script setup>
const links = [
  { href: '#knowledge', label: '牙齿知识' },
  { href: '#routine', label: '护理流程' },
  { href: '#tools', label: '工具大全' },
  { href: '#plans', label: '人群方案' },
  { href: '#faq', label: '常见误区' }
]
</script>

<template>
  <header class="nav">
    <div class="nav__inner">
      <a class="nav__logo" href="#top">🦷 <span>口腔科普</span></a>
      <nav class="nav__links">
        <a v-for="l in links" :key="l.href" :href="l.href">{{ l.label }}</a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.nav {
  position: sticky;
  top: 0;
  z-index: 50;
  backdrop-filter: blur(12px);
  background: rgba(255, 255, 255, 0.78);
  border-bottom: 1px solid var(--line);
}
.nav__inner {
  max-width: 1080px;
  margin: 0 auto;
  padding: 12px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
}
.nav__logo {
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--brand);
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 6px;
  white-space: nowrap;
}
.nav__links {
  display: flex;
  gap: 6px;
  overflow-x: auto;
}
.nav__links a {
  color: var(--text-2);
  text-decoration: none;
  font-size: 0.92rem;
  padding: 6px 12px;
  border-radius: 999px;
  white-space: nowrap;
  transition: 0.2s;
}
.nav__links a:hover {
  background: var(--brand-soft);
  color: var(--brand);
}
</style>
