<script setup>
const morning = [
  { step: '1', title: '温水漱口', text: '唤醒口腔，简单冲走夜间堆积的分泌物。' },
  { step: '2', title: '刷牙 2 分钟', text: '软毛 / 电动牙刷，45° 对准牙龈沟，分区刷全。' },
  { step: '3', title: '舌面清洁', text: '用刮舌器轻刮舌背，改善口气。' },
  { step: '4', title: '漱口收尾', text: '必要时使用漱口水，含漱 30 秒。' }
]
const night = [
  { step: '1', title: '牙线 / 牙缝刷', text: '先清牙缝！邻面菌斑是蛀牙和牙周炎高发区。' },
  { step: '2', title: '刷牙 2 分钟', text: '睡前这次最重要，夜间唾液少、细菌更活跃。' },
  { step: '3', title: '冲牙器冲洗', text: '低档脉冲冲洗牙缝、牙龈沟、矫正器周围。' },
  { step: '4', title: '之后不再进食', text: '刷完牙后只喝白水，避免前功尽弃。' }
]
</script>

<template>
  <section class="section section--tint" id="routine">
    <div class="wrap">
      <div class="section__head">
        <p class="section__eyebrow">02 · 日常流程</p>
        <h2 class="section__title">一套标准的早晚护理流程</h2>
        <p class="section__desc">顺序比想象中重要：先清牙缝，再刷牙，最后冲洗。</p>
      </div>

      <div class="routine">
        <div class="routine__col routine__col--morning">
          <div class="routine__badge">☀️ 早晨</div>
          <ol class="steps">
            <li v-for="item in morning" :key="item.title">
              <span class="steps__dot">{{ item.step }}</span>
              <div>
                <h4>{{ item.title }}</h4>
                <p>{{ item.text }}</p>
              </div>
            </li>
          </ol>
        </div>

        <div class="routine__col routine__col--night">
          <div class="routine__badge">🌙 睡前</div>
          <ol class="steps">
            <li v-for="item in night" :key="item.title">
              <span class="steps__dot">{{ item.step }}</span>
              <div>
                <h4>{{ item.title }}</h4>
                <p>{{ item.text }}</p>
              </div>
            </li>
          </ol>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.routine {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
.routine__col {
  background: #fff;
  border: 1px solid var(--line);
  border-radius: 20px;
  padding: 26px 24px 10px;
  position: relative;
  overflow: hidden;
}
.routine__col::before {
  content: '';
  position: absolute;
  inset: 0 0 auto 0;
  height: 4px;
}
.routine__col--morning::before { background: linear-gradient(90deg, #ffc861, #ff9e4d); }
.routine__col--night::before { background: linear-gradient(90deg, #6aa8ff, #22b58a); }
.routine__badge {
  display: inline-block;
  font-weight: 700;
  font-size: 1rem;
  margin-bottom: 18px;
}
.steps {
  list-style: none;
  margin: 0;
  padding: 0;
}
.steps li {
  display: flex;
  gap: 14px;
  padding-bottom: 18px;
  position: relative;
}
.steps li:not(:last-child)::before {
  content: '';
  position: absolute;
  left: 14px;
  top: 30px;
  bottom: 2px;
  width: 2px;
  background: var(--line);
}
.steps__dot {
  flex: 0 0 30px;
  height: 30px;
  border-radius: 50%;
  background: var(--brand-soft);
  color: var(--brand);
  font-weight: 700;
  font-size: 0.9rem;
  display: grid;
  place-items: center;
  z-index: 1;
}
.steps h4 {
  margin: 3px 0 4px;
  font-size: 0.98rem;
  color: var(--text-1);
}
.steps p {
  margin: 0;
  font-size: 0.88rem;
  color: var(--text-2);
  line-height: 1.65;
}
@media (max-width: 720px) {
  .routine { grid-template-columns: 1fr; }
}
</style>
