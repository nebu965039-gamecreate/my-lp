<script setup>
import { ref } from 'vue'

const billing = ref('monthly') // 'monthly' | 'yearly'

const plans = [
  {
    key: 'free', name: 'フリー', desc: 'はじめての方に',
    monthly: 0, yearly: 0,
    features: ['予約は月20件まで', '基本のオンライン予約フォーム', 'カレンダー表示'],
  },
  {
    key: 'standard', name: 'スタンダード', desc: '個人サロン・教室向け',
    monthly: 2980, yearly: 27800, featured: true,
    features: ['予約数は無制限', 'LINE・メールの自動リマインド', '売上レポート', '顧客カルテの保存'],
  },
  {
    key: 'pro', name: 'プロ', desc: '複数スタッフ・複数店舗',
    monthly: 5980, yearly: 55800,
    features: ['スタッフ・席ごとの予約管理', 'LINE公式アカウント連携', '優先サポート対応', '複数店舗の一括管理'],
  },
]

// 年払い選択時、「月あたりいくらか」に換算して表示する
const yearlyMonthlyEquivalent = (plan) => Math.round(plan.yearly / 12)
</script>

<template>
  <section class="pricing wrap reveal" id="pricing">
    <p class="eyebrow">Pricing</p>
    <h2 class="section-title">お店の規模に合わせて選べる料金</h2>
    <p class="section-lede">まずはフリープランから。育ってきたらいつでも切り替えられます。</p>

    <div class="pricing-toggle">
      <button :class="{ active: billing === 'monthly' }" @click="billing = 'monthly'">月払い</button>
      <button :class="{ active: billing === 'yearly' }" @click="billing = 'yearly'">年払い</button>
      <span class="save-badge" v-if="billing === 'yearly'">2ヶ月分お得</span>
    </div>

    <div class="plan-grid">
      <div v-for="p in plans" :key="p.key" class="plan-card" :class="{ featured: p.featured }">
        <p class="plan-name">{{ p.name }}</p>
        <p class="plan-desc">{{ p.desc }}</p>

        <p class="plan-price">
          <template v-if="p.monthly === 0">¥0</template>
          <template v-else-if="billing === 'monthly'">¥{{ p.monthly.toLocaleString() }}<span>/月</span></template>
          <template v-else>¥{{ yearlyMonthlyEquivalent(p).toLocaleString() }}<span>/月</span></template>
        </p>

        <p class="plan-period" v-if="p.monthly !== 0 && billing === 'yearly'">年額 ¥{{ p.yearly.toLocaleString() }}（一括）</p>
        <p class="plan-period" v-else-if="p.monthly !== 0">月ごとのお支払い</p>
        <p class="plan-period" v-else>ずっと無料</p>

        <ul class="plan-features">
          <li v-for="f in p.features" :key="f">{{ f }}</li>
        </ul>

        <a href="#contact" class="btn" :class="p.featured ? 'btn-stamp' : 'btn-ghost'">このプランで始める</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.pricing { padding: 80px 0; }
.pricing-toggle {
  display: inline-flex;
  align-items: center;
  gap: 14px;
  background: var(--color-surface);
  border: 1px solid var(--color-line);
  padding: 6px;
  border-radius: 30px;
  margin: 28px 0 8px;
}
.pricing-toggle button {
  border: none;
  background: transparent;
  padding: 9px 18px;
  border-radius: 24px;
  font-weight: 700;
  font-size: 13.5px;
  cursor: pointer;
  color: var(--color-ink-soft);
  transition: all .18s ease;
}
.pricing-toggle button.active { background: var(--color-ink); color: #fff; }
.save-badge {
  font-family: var(--font-mono);
  font-size: 11.5px;
  background: var(--color-stamp-soft);
  color: var(--color-stamp);
  padding: 4px 10px;
  border-radius: 20px;
  font-weight: 700;
}
.plan-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-top: 32px;
}
.plan-card {
  background: var(--color-surface);
  border-radius: var(--radius-card);
  border: 1.5px solid var(--color-line);
  padding: 30px 26px;
  display: flex;
  flex-direction: column;
}
.plan-card.featured {
  border-color: var(--color-stamp);
  box-shadow: 0 16px 36px rgba(188, 75, 60, .14);
  position: relative;
}
.plan-card.featured::before {
  content: "おすすめ";
  position: absolute;
  top: -12px;
  right: 24px;
  background: var(--color-stamp);
  color: #fff;
  font-size: 11.5px;
  font-weight: 700;
  padding: 4px 12px;
  border-radius: 20px;
  font-family: var(--font-mono);
}
.plan-name { font-family: var(--font-display); font-weight: 700; font-size: 18px; margin-bottom: 4px; }
.plan-desc { font-size: 13px; color: var(--color-ink-soft); margin-bottom: 18px; }
.plan-price { font-family: var(--font-mono); font-size: 32px; font-weight: 700; margin-bottom: 4px; }
.plan-price span { font-size: 13px; font-weight: 400; color: var(--color-ink-faint); }
.plan-period { font-size: 12px; color: var(--color-ink-faint); margin-bottom: 20px; font-family: var(--font-mono); }
.plan-features { list-style: none; padding: 0; margin: 0 0 24px; flex: 1; }
.plan-features li { font-size: 13.5px; color: var(--color-ink-soft); padding-left: 20px; position: relative; margin-bottom: 10px; }
.plan-features li::before { content: "✓"; position: absolute; left: 0; color: var(--color-stamp); font-weight: 700; }

@media (max-width: 860px) {
  .plan-grid { grid-template-columns: 1fr; }
}
</style>
