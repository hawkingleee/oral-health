<script setup>
import { computed, ref } from 'vue'
import { tools } from '../data.js'

const filters = [
  { id: 'all', label: '全部工具' },
  { id: 'clean', label: '基础清洁' },
  { id: 'inter', label: '邻面清洁' },
  { id: 'gum', label: '牙龈护理' },
  { id: 'fresh', label: '清新口气' }
]
const active = ref('all')
const openId = ref(null)

const list = computed(() =>
  active.value === 'all'
    ? tools
    : tools.filter((t) => t.tags.includes(active.value))
)

function toggle(id) {
  openId.value = openId.value === id ? null : id
}

const tagMeta = {
  clean: { label: '基础清洁', color: '#1f8fe0', bg: '#e7f3fd' },
  inter: { label: '邻面清洁', color: '#8a5cf6', bg: '#f0eafe' },
  gum: { label: '牙龈护理', color: '#e0644d', bg: '#fdeeea' },
  fresh: { label: '清新口气', color: '#12a97a', bg: '#e4f8f0' }
}
</script>

<template>
  <section class="section" id="tools">
    <div class="wrap">
      <div class="section__head">
        <p class="section__eyebrow">03 · 核心内容</p>
        <h2 class="section__title">每块区域，该用哪件工具？</h2>
        <p class="section__desc">
          牙刷负责牙齿表面，牙线 / 牙缝刷负责邻面，冲牙器冲洗死角，漱口水只做辅助。
          点击卡片展开使用方法。
        </p>
      </div>

      <div class="filters">
        <button
          v-for="f in filters"
          :key="f.id"
          class="filter"
          :class="{ 'filter--on': active === f.id }"
          @click="active = f.id"
        >
          {{ f.label }}
        </button>
      </div>

      <div class="tools">
        <article
          v-for="t in list"
          :key="t.id"
          class="tool"
          :class="{ 'tool--open': openId === t.id }"
        >
          <header class="tool__head" @click="toggle(t.id)">
            <div class="tool__emoji">{{ t.emoji }}</div>
            <div class="tool__meta">
              <h3>{{ t.name }}</h3>
              <p>{{ t.tagline }}</p>
            </div>
            <div class="tool__level" :title="`推荐指数 ${t.level}/5`">
              <span v-for="i in 5" :key="i" :class="{ on: i <= t.level }">●</span>
            </div>
            <span class="tool__arrow">{{ openId === t.id ? '−' : '+' }}</span>
          </header>

          <div class="tool__tags">
            <span
              v-for="tag in t.tags"
              :key="tag"
              class="chip"
              :style="{ color: tagMeta[tag].color, background: tagMeta[tag].bg }"
            >
              {{ tagMeta[tag].label }}
            </span>
          </div>

          <p class="tool__desc">{{ t.desc }}</p>

          <transition name="expand">
            <div v-if="openId === t.id" class="tool__detail">
              <div class="detail-block">
                <h4>适用人群</h4>
                <ul>
                  <li v-for="x in t.fit" :key="x">{{ x }}</li>
                </ul>
              </div>
              <div class="detail-block">
                <h4>怎么用</h4>
                <ol>
                  <li v-for="x in t.how" :key="x">{{ x }}</li>
                </ol>
              </div>
              <div class="detail-tip">💡 {{ t.tip }}</div>
            </div>
          </transition>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.filters {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 24px;
}
.filter {
  border: 1px solid var(--line);
  background: #fff;
  color: var(--text-2);
  padding: 8px 18px;
  border-radius: 999px;
  font-size: 0.9rem;
  cursor: pointer;
  transition: 0.2s;
  font-family: inherit;
}
.filter:hover { border-color: #bfe1f7; color: var(--brand); }
.filter--on {
  background: var(--brand);
  border-color: var(--brand);
  color: #fff;
  box-shadow: 0 8px 18px rgba(31, 143, 224, 0.28);
}
.tools {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 18px;
  align-items: start;
}
.tool {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 20px;
  padding: 22px;
  transition: 0.25s;
}
.tool:hover { border-color: #bfe1f7; box-shadow: 0 14px 30px rgba(20, 60, 100, 0.08); }
.tool--open { grid-column: 1 / -1; }
.tool__head {
  display: flex;
  align-items: center;
  gap: 14px;
  cursor: pointer;
  user-select: none;
}
.tool__emoji {
  flex: 0 0 52px;
  height: 52px;
  border-radius: 14px;
  background: var(--brand-soft);
  display: grid;
  place-items: center;
  font-size: 1.6rem;
}
.tool__meta { flex: 1; min-width: 0; }
.tool__meta h3 { margin: 0; font-size: 1.12rem; color: var(--text-1); }
.tool__meta p { margin: 3px 0 0; font-size: 0.84rem; color: var(--text-3); }
.tool__level { display: flex; gap: 2px; font-size: 0.6rem; }
.tool__level span { color: #dde5ec; }
.tool__level span.on { color: #ffb937; }
.tool__arrow {
  flex: 0 0 30px;
  height: 30px;
  border-radius: 50%;
  background: #f1f5f9;
  color: var(--text-2);
  display: grid;
  place-items: center;
  font-size: 1.2rem;
  line-height: 1;
}
.tool__tags { display: flex; flex-wrap: wrap; gap: 8px; margin: 16px 0 12px; }
.chip {
  font-size: 0.76rem;
  padding: 4px 11px;
  border-radius: 999px;
  font-weight: 600;
}
.tool__desc {
  margin: 0;
  color: var(--text-2);
  font-size: 0.92rem;
  line-height: 1.75;
}
.tool__detail {
  margin-top: 20px;
  padding-top: 20px;
  border-top: 1px dashed var(--line);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 22px;
}
.detail-block h4 {
  margin: 0 0 10px;
  font-size: 0.92rem;
  color: var(--brand);
}
.detail-block ul,
.detail-block ol {
  margin: 0;
  padding-left: 18px;
  color: var(--text-2);
  font-size: 0.9rem;
  line-height: 1.9;
}
.detail-tip {
  grid-column: 1 / -1;
  background: #fffaf0;
  border: 1px solid #ffe6b0;
  border-radius: 12px;
  padding: 14px 16px;
  font-size: 0.88rem;
  color: #8a6414;
  line-height: 1.7;
}
.expand-enter-active,
.expand-leave-active { transition: all 0.25s ease; }
.expand-enter-from,
.expand-leave-to { opacity: 0; transform: translateY(-6px); }
@media (max-width: 720px) {
  .tool__detail { grid-template-columns: 1fr; }
}
</style>
