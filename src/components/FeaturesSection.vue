<script setup>
const features = [
  {
    icon: '◎',
    title: '予約はカレンダーひとつで完結',
    body: 'お客様はオンラインで空いている時間を選ぶだけ。電話対応に追われることがなくなります。',
  },
  {
    icon: '◇',
    title: 'リマインドは自動でお届け',
    body: '前日の夜と当日の朝、LINEとメールで自動通知。無断キャンセルがぐっと減ります。',
  },
  {
    icon: '□',
    title: '台帳とExcelを卒業',
    body: '来店履歴や売上を自動で記録。紙の台帳とExcelの二重管理から解放されます。',
  },
]
</script>

<template>
  <section class="features wrap reveal" id="features">
    <p class="eyebrow">Features</p>
    <h2 class="section-title">毎日の「予約まわり」を、3つでまとめて。</h2>
    <p class="section-lede">電話・紙・LINEに分かれていた予約業務を、ひとつの画面に。</p>

    <div class="feature-grid">
      <div class="feature-card" v-for="f in features" :key="f.title">
        <div class="ico">{{ f.icon }}</div>
        <h3>{{ f.title }}</h3>
        <p>{{ f.body }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.features { padding: 78px 0; }
.feature-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-top: 36px;
}
.feature-card {
  background: var(--color-surface);
  border-radius: var(--radius-card);
  padding: 26px 22px;
  border: 1px solid var(--color-line);
  position: relative;
}
.feature-card .ico {
  width: 42px;
  height: 42px;
  border-radius: 10px;
  background: var(--color-stamp-soft);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 16px;
  color: var(--color-stamp);
}
.feature-card h3 { font-family: var(--font-display); font-size: 18px; margin: 0 0 8px; }
.feature-card p { font-size: 14px; color: var(--color-ink-soft); margin: 0; }

@media (max-width: 860px) {
  .feature-grid { grid-template-columns: 1fr; }
}
</style>
