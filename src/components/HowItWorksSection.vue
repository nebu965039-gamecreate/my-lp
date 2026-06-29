<script setup>
const steps = [
  { num: '01', title: '空き時間を登録', body: '営業日と施術時間を一度設定するだけ。' },
  { num: '02', title: 'オンラインで予約', body: 'お客様は24時間いつでも好きな時間に予約できます。' },
  { num: '03', title: '自動でリマインド', body: '前日と当日にLINE・メールでお知らせします。' },
  { num: '04', title: '来店・次回予約', body: 'その場で次回の予約もスムーズにご案内できます。' },
]
</script>

<template>
  <section class="how wrap reveal" id="how">
    <p class="eyebrow">How it works</p>
    <h2 class="section-title">導入から運用まで、4つのステップ</h2>

    <div class="how-grid">
      <div class="how-step" v-for="s in steps" :key="s.num">
        <div class="how-num">{{ s.num }}</div>
        <h4>{{ s.title }}</h4>
        <p>{{ s.body }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.how {
  padding: 78px 0;
  background: var(--color-surface);
  border-top: 1px solid var(--color-line);
  border-bottom: 1px solid var(--color-line);
}
.how-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0;
  margin-top: 40px;
  position: relative;
}
.how-step { padding: 0 20px; position: relative; }
.how-step:not(:last-child)::after {
  content: "";
  position: absolute;
  top: 18px;
  right: -2px;
  width: 100%;
  height: 1px;
  border-top: 2px dashed var(--color-line);
}
.how-num {
  font-family: var(--font-mono);
  font-weight: 700;
  font-size: 13px;
  color: var(--color-stamp);
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: 1.5px solid var(--color-stamp);
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--color-bg);
  position: relative;
  z-index: 2;
  margin-bottom: 16px;
}
.how-step h4 { font-size: 15.5px; margin: 0 0 6px; font-weight: 700; }
.how-step p { font-size: 13.5px; color: var(--color-ink-soft); margin: 0; }

@media (max-width: 860px) {
  .how-grid { grid-template-columns: 1fr 1fr; gap: 28px; }
  .how-step:not(:last-child)::after { display: none; }
}
</style>
