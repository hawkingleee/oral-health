<script setup>
import { facts } from '../data.js'
</script>

<template>
  <section class="section" id="knowledge">
    <div class="wrap">
      <div class="section__head">
        <p class="section__eyebrow">01 · 先懂原理</p>
        <h2 class="section__title">关于牙齿，你需要知道的几件事</h2>
        <p class="section__desc">理解口腔的运作规律，才知道为什么要这样护理。</p>
      </div>

      <div class="facts">
        <article v-for="f in facts" :key="f.title" class="fact">
          <div class="fact__icon">{{ f.icon }}</div>
          <h3>{{ f.title }}</h3>
          <p>{{ f.text }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.facts {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 18px;
}
.fact {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 18px;
  padding: 24px 22px;
  transition: 0.25s;
}
.fact:hover {
  transform: translateY(-4px);
  box-shadow: 0 16px 34px rgba(20, 60, 100, 0.1);
  border-color: #bfe1f7;
}
.fact__icon {
  font-size: 1.9rem;
  margin-bottom: 12px;
}
.fact h3 {
  margin: 0 0 8px;
  font-size: 1.08rem;
  color: var(--text-1);
}
.fact p {
  margin: 0;
  color: var(--text-2);
  font-size: 0.93rem;
  line-height: 1.75;
}
</style>
