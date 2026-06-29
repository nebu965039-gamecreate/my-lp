<script setup>
import { ref, onMounted } from 'vue'

// ページを開いてから少し遅れて「確認済」のスタンプが押される、唯一の演出ポイント
const stampShown = ref(false)
onMounted(() => {
  setTimeout(() => { stampShown.value = true }, 450)
})
</script>

<template>
  <section class="hero wrap">
    <div class="hero-grid">
      <div>
        <p class="eyebrow">個人サロン・教室・士業のための予約管理</p>
        <h1>
          予約のことは、<br />
          <span class="accent">まいど</span>におまかせ。
        </h1>
        <p class="lede">
          電話対応に追われる毎日、紙の台帳の書き間違い。<br />
          オンライン予約とリマインド送信を、ひとつにまとめます。
        </p>
        <div class="hero-actions">
          <a href="#pricing" class="btn btn-stamp">無料で試す</a>
          <a href="#how" class="btn btn-ghost">使い方を見る</a>
        </div>
        <p class="hero-note">クレジットカード登録不要 ・ 1分で開始</p>
      </div>

      <div>
        <div class="ticket">
          <div class="ticket-main">
            <p class="ticket-label">Reservation</p>
            <p class="ticket-shop">Atelier Mori</p>
            <div class="ticket-row"><span>日時</span><span>6/29（月）14:00</span></div>
            <div class="ticket-row"><span>メニュー</span><span>カラー＋カット</span></div>
            <div class="ticket-row"><span>お客様</span><span>T. Yamada</span></div>
            <div class="ticket-row"><span>所要時間</span><span>90 min</span></div>
          </div>
          <div class="ticket-stub">
            <div class="stamp" :class="{ show: stampShown }">確認済</div>
            <span class="num">No. 0142</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero { padding: 68px 0 84px; }
.hero-grid {
  display: grid;
  grid-template-columns: 1.1fr .9fr;
  gap: 56px;
  align-items: center;
}
.hero h1 {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: clamp(34px, 4.6vw, 54px);
  line-height: 1.32;
  margin: 14px 0 18px;
}
.hero h1 .accent { color: var(--color-stamp); }
.hero p.lede {
  font-size: 16.5px;
  color: var(--color-ink-soft);
  max-width: 460px;
  margin-bottom: 30px;
}
.hero-actions {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 26px;
}
.hero-note {
  font-size: 13px;
  color: var(--color-ink-faint);
  font-family: var(--font-mono);
}

.ticket {
  position: relative;
  background: var(--color-surface);
  border-radius: var(--radius-card);
  box-shadow: 0 18px 40px rgba(31, 42, 68, .12);
  display: grid;
  grid-template-columns: 1fr 96px;
  overflow: hidden;
  transform: rotate(1.2deg);
}
.ticket-main { padding: 26px 24px; border-right: 2px dashed var(--color-line); }
.ticket-label {
  font-family: var(--font-mono);
  font-size: 11px;
  letter-spacing: .08em;
  color: var(--color-ink-faint);
  text-transform: uppercase;
}
.ticket-shop { font-family: var(--font-display); font-weight: 700; font-size: 20px; margin: 6px 0 14px; }
.ticket-row { display: flex; justify-content: space-between; font-size: 13.5px; margin-bottom: 8px; color: var(--color-ink-soft); }
.ticket-row span:last-child { font-family: var(--font-mono); color: var(--color-ink); font-weight: 700; }
.ticket-stub {
  background: var(--color-stamp-soft);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 10px;
  position: relative;
}
.ticket-stub .num { font-family: var(--font-mono); font-size: 12px; color: var(--color-ink-faint); writing-mode: vertical-rl; }
.stamp {
  width: 62px;
  height: 62px;
  border-radius: 50%;
  border: 2.5px solid var(--color-stamp);
  color: var(--color-stamp);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 12px;
  transform: rotate(-14deg) scale(0);
  opacity: 0;
  transition: transform .5s cubic-bezier(.2, 1.4, .4, 1), opacity .3s ease;
  text-align: center;
  line-height: 1.2;
}
.stamp.show { transform: rotate(-14deg) scale(1); opacity: 1; }

@media (max-width: 860px) {
  .hero-grid { grid-template-columns: 1fr; }
}
</style>
