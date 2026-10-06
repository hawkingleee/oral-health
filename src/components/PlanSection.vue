<script setup>
import { computed, ref } from 'vue'
import { plans, tools } from '../data.js'

const activeId = ref(plans[0].id)
const active = computed(() => plans.find((p) => p.id === activeId.value))

function toolById(id) {
  return tools.find((t) => t.id === id)
}
</script>

<template>
  <section class="section section--tint" id="plans">
    <div class="wrap">
      <div class="section__head">
        <p class="section__eyebrow">04 · 对症选配</p>
        <h2 class="section__title">不同人群，搭配不同</h2>
        <p class="section__desc">选择你的情况，看看推荐的工具组合与护理重点。</p>
      </div>

      <div class="tabs">
        <button
          v-for="p in plans"
          :key="p.id"
          class="tab"
          :class="{ 'tab--on': activeId === p.id }"
          @click="activeId = p.id"
        >
          <span class="tab__emoji">{{ p.emoji }}</span>
          {{ p.name }}
        </button>
      </div>

      <div class="panel">
        <div class="panel__tools">
          <h3>{{ active.emoji }} {{ active.name }} · 推荐工具</h3>
          <div class="panel__grid">
            <div v-for="id in active.tools" :key="id" class="ptool">
              <span class="ptool__emoji">{{ toolById(id).emoji }}</span>
              <div>
                <strong>{{ toolById(id).name }}</strong>
                <small>{{ toolById(id).tagline }}</small>
              </div>
            </div>
          </div>
        </div>

        <div class="panel__steps">
          <h3>✅ 护理重点</h3>
          <ul>
            <li v-for="s in active.steps" :key="s">{{ s }}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 22px;
}
.tab {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  border: 1px solid var(--line);
  background: #fff;
  padding: 10px 18px;
  border-radius: 999px;
  font-size: 0.92rem;
  color: var(--text-2);
  cursor: pointer;
  transition: 0.2s;
  font-family: inherit;
}
.tab:hover { border-color: #bfe1f7; color: var(--brand); }
.tab--on {
  background: linear-gradient(120deg, #1f8fe0, #22b58a);
  border-color: transparent;
  color: #fff;
  box-shadow: 0 10px 22px rgba(31, 143, 224, 0.3);
}
.tab__emoji { font-size: 1.05rem; }
.panel {
  display: grid;
  grid-template-columns: 1.1fr 1fr;
  gap: 20px;
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 22px;
  padding: 28px;
}
.panel h3 {
  margin: 0 0 16px;
  font-size: 1.05rem;
  color: var(--text-1);
}
.panel__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 12px;
}
.ptool {
  display: flex;
  align-items: center;
  gap: 12px;
  background: var(--brand-soft);
  border-radius: 14px;
  padding: 14px;
}
.ptool__emoji { font-size: 1.4rem; }
.ptool strong { display: block; font-size: 0.95rem; color: var(--text-1); }
.ptool small { color: var(--text-3); font-size: 0.78rem; }
.panel__steps {
  border-left: 1px dashed var(--line);
  padding-left: 24px;
}
.panel__steps ul {
  margin: 0;
  padding-left: 20px;
  color: var(--text-2);
  line-height: 2;
  font-size: 0.93rem;
}
@media (max-width: 760px) {
  .panel { grid-template-columns: 1fr; }
  .panel__steps { border-left: none; padding-left: 0; border-top: 1px dashed var(--line); padding-top: 20px; }
}
</style>
