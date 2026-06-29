<template>
  <footer class="wrap">
    <div class="footer-grid">
      <a href="#top" class="brand"><span class="mark">舗</span>まいど</a>
      <ul class="footer-links">
        <li><a href="#features">機能</a></li>
        <li><a href="#pricing">料金</a></li>
        <li><a href="#faq">よくある質問</a></li>
        <li><a href="#contact">お問い合わせ</a></li>
      </ul>
    </div>
    <p class="footer-fine">© 2026 Maido, Inc. ― これはポートフォリオ用のデモサイトです。</p>
  </footer>
</template>

<style scoped>
footer { padding: 40px 0 50px; border-top: 1px solid var(--color-line); }
.footer-grid { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 16px; }
.brand {
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: var(--font-display);
  font-weight: 700;
  font-size: 17px;
  text-decoration: none;
  color: var(--color-ink);
}
.brand .mark {
  width: 30px;
  height: 30px;
  border-radius: 8px;
  background: var(--color-ink);
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-mono);
  font-size: 13px;
  font-weight: 700;
  transform: rotate(-4deg);
}
.footer-links { display: flex; gap: 22px; list-style: none; margin: 0; padding: 0; font-size: 13px; color: var(--color-ink-soft); }
.footer-links a { text-decoration: none; }
.footer-fine { font-size: 12px; color: var(--color-ink-faint); margin-top: 18px; font-family: var(--font-mono); }
</style>
