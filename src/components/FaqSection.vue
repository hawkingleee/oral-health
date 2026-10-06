<script setup>
import { ref } from 'vue'
import { faqs } from '../data.js'

const openIndex = ref(0)
function toggle(i) {
  openIndex.value = openIndex.value === i ? -1 : i
}
</script>

<template>
  <section class="section" id="faq">
    <div class="wrap wrap--narrow">
      <div class="section__head">
        <p class="section__eyebrow">05 · 别踩坑</p>
        <h2 class="section__title">常见误区答疑</h2>
        <p class="section__desc">这些说法你是不是也听过？看看真相是什么。</p>
      </div>

      <div class="faq">
        <div
          v-for="(f, i) in faqs"
          :key="i"
          class="qa"
          :class="{ 'qa--open': openIndex === i }"
        >
          <button class="qa__q" @click="toggle(i)">
            <span>{{ f.q }}</span>
            <span class="qa__icon">{{ openIndex === i ? '−' : '+' }}</span>
          </button>
          <transition name="expand">
            <div v-show="openIndex === i" class="qa__a">{{ f.a }}</div>
          </transition>
        </div>
      </div>

      <div class="notice">
        <strong>⚠️ 温馨提醒</strong>
        <p>
          以上内容仅供科普参考，不能替代专业诊断。若出现持续牙龈出血、牙齿松动、
          剧烈疼痛、口腔溃疡两周不愈等情况，请及时到正规口腔机构就诊。
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.faq {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.qa {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 16px;
  overflow: hidden;
  transition: 0.2s;
}
.qa--open { border-color: #bfe1f7; box-shadow: 0 12px 26px rgba(20, 60, 100, 0.07); }
.qa__q {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  background: none;
  border: none;
  padding: 18px 20px;
  font-size: 1rem;
  font-weight: 600;
  color: var(--text-1);
  text-align: left;
  cursor: pointer;
  font-family: inherit;
}
.qa__icon {
  flex: 0 0 26px;
  height: 26px;
  border-radius: 50%;
  background: var(--brand-soft);
  color: var(--brand);
  display: grid;
  place-items: center;
  font-size: 1.1rem;
  line-height: 1;
}
.qa__a {
  padding: 0 20px 20px;
  color: var(--text-2);
  font-size: 0.93rem;
  line-height: 1.85;
}
.expand-enter-active,
.expand-leave-active { transition: all 0.25s ease; }
.expand-enter-from,
.expand-leave-to { opacity: 0; transform: translateY(-6px); }
.notice {
  margin-top: 28px;
  background: #fff6f6;
  border: 1px solid #ffd9d9;
  border-radius: 16px;
  padding: 20px 22px;
}
.notice strong { color: #d9534f; }
.notice p {
  margin: 8px 0 0;
  color: #8a5555;
  font-size: 0.9rem;
  line-height: 1.8;
}
</style>
