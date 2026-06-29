<script setup>
import { ref } from 'vue'

const faqs = ref([
  {
    q: '今使っている予約ノートやExcelからの引っ越しはできますか？',
    a: 'CSVでお客様情報を一括インポートできます。データ量が多い場合は移行をサポートするプランもご用意しています。',
    open: true,
  },
  {
    q: '無料プランはいつまで使えますか？',
    a: '期間の制限はありません。予約件数が月20件を超えたタイミングでアップグレードをご検討ください。',
    open: false,
  },
  {
    q: 'LINEでのリマインドは追加料金がかかりますか？',
    a: 'スタンダードプラン以上であれば、追加料金なしでご利用いただけます。',
    open: false,
  },
  {
    q: '解約はいつでもできますか？',
    a: 'いつでも解約可能です。年額プランは残り期間分の返金には対応していませんが、違約金は発生しません。',
    open: false,
  },
])

const toggleFaq = (i) => {
  faqs.value[i].open = !faqs.value[i].open
}
</script>

<template>
  <section class="faq wrap reveal" id="faq">
    <p class="eyebrow">FAQ</p>
    <h2 class="section-title">よくある質問</h2>

    <div class="faq-list">
      <div class="faq-item" v-for="(item, i) in faqs" :key="item.q">
        <button class="faq-q" :aria-expanded="item.open" @click="toggleFaq(i)">
          {{ item.q }}
          <span class="plus">＋</span>
        </button>
        <div class="faq-a" :style="{ maxHeight: item.open ? '200px' : '0px' }">
          <div class="faq-a-inner">{{ item.a }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.faq {
  padding: 80px 0;
  background: var(--color-surface);
  border-top: 1px solid var(--color-line);
  border-bottom: 1px solid var(--color-line);
}
.faq-list { max-width: 680px; margin-top: 32px; }
.faq-item { border-bottom: 1px solid var(--color-line); }
.faq-q {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
  padding: 20px 4px;
  cursor: pointer;
  font-weight: 700;
  font-size: 15.5px;
  background: none;
  border: none;
  width: 100%;
  text-align: left;
  color: var(--color-ink);
}
.faq-q .plus {
  font-family: var(--font-mono);
  font-size: 18px;
  color: var(--color-stamp);
  flex-shrink: 0;
  transition: transform .2s ease;
}
.faq-q[aria-expanded="true"] .plus { transform: rotate(45deg); }
.faq-a { overflow: hidden; transition: max-height .25s ease; }
.faq-a-inner { padding: 0 4px 20px; font-size: 14px; color: var(--color-ink-soft); max-width: 560px; }
</style>
