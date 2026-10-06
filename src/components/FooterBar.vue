<template>
  <footer class="footer">
    <div class="wrap footer__inner">
      <div>
        <p class="footer__logo">🦷 口腔科普</p>
        <p class="footer__slogan">科学护牙，从小习惯开始。</p>
      </div>
      <p class="footer__copy">
        © {{ new Date().getFullYear() }} 口腔健康科普 · 内容仅供学习参考，请以专业医师建议为准
      </p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: #0f2a3f;
  color: #b7cddd;
  padding: 40px 20px;
  margin-top: 40px;
}
.footer__inner {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  gap: 20px;
  flex-wrap: wrap;
}
.footer__logo { margin: 0; font-size: 1.1rem; font-weight: 700; color: #fff; }
.footer__slogan { margin: 8px 0 0; font-size: 0.88rem; }
.footer__copy { margin: 0; font-size: 0.8rem; opacity: 0.7; }
</style>
