<template>
  <header class="site">
    <nav class="nav wrap">
      <a href="#top" class="brand"><span class="mark">舗</span>まいど</a>
      <ul class="nav-links">
        <li><a href="#features">機能</a></li>
        <li><a href="#how">使い方</a></li>
        <li><a href="#pricing">料金</a></li>
        <li><a href="#faq">よくある質問</a></li>
      </ul>
      <div class="nav-cta">
        <a href="#contact" class="btn btn-ghost">お問い合わせ</a>
        <a href="#pricing" class="btn btn-primary">無料で試す</a>
      </div>
    </nav>
  </header>
</template>

<style scoped>
header.site {
  position: sticky;
  top: 0;
  z-index: 40;
  background: rgba(245, 243, 236, .88);
  backdrop-filter: blur(8px);
  border-bottom: 1px solid var(--color-line);
}
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 24px;
}
.brand {
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: var(--font-display);
  font-weight: 700;
  font-size: 21px;
  text-decoration: none;
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
.nav-links {
  display: flex;
  gap: 28px;
  list-style: none;
  margin: 0;
  padding: 0;
}
.nav-links a {
  text-decoration: none;
  font-size: 14.5px;
  font-weight: 500;
  color: var(--color-ink-soft);
  transition: color .15s ease;
}
.nav-links a:hover { color: var(--color-ink); }
.nav-cta {
  display: flex;
  gap: 10px;
  align-items: center;
}
</style>
