<script setup>
import { ref } from 'vue'

const form = ref({ shop: '', name: '', email: '', message: '' })
const errors = ref({})
const submitted = ref(false)

const validate = () => {
  const e = {}
  if (!form.value.shop.trim()) e.shop = 'お店・教室の名前を入力してください'
  if (!form.value.name.trim()) e.name = 'お名前を入力してください'
  if (!form.value.email.trim()) {
    e.email = 'メールアドレスを入力してください'
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.value.email)) {
    e.email = 'メールアドレスの形式が正しくありません'
  }
  if (!form.value.message.trim()) e.message = 'お問い合わせ内容を入力してください'

  errors.value = e
  return Object.keys(e).length === 0
}

const submit = () => {
  // デモのため実際の送信処理は行わず、画面の状態だけ切り替える
  if (validate()) {
    submitted.value = true
  }
}
</script>

<template>
  <section class="contact wrap reveal" id="contact">
    <p class="eyebrow">Contact</p>
    <h2 class="section-title">資料が欲しい・相談したい方はこちら</h2>

    <div class="contact-grid">
      <div>
        <p class="section-lede">
          導入のご相談、料金プランのご質問、デモのご依頼など、お気軽にお問い合わせください。1営業日以内にご返信します。
        </p>
      </div>

      <div class="contact-card">
        <template v-if="!submitted">
          <div class="field" :class="{ error: errors.shop }">
            <label>お店・教室の名前</label>
            <input v-model="form.shop" type="text" placeholder="例：Atelier Mori" />
            <p class="err-msg" v-if="errors.shop">{{ errors.shop }}</p>
          </div>

          <div class="field" :class="{ error: errors.name }">
            <label>お名前</label>
            <input v-model="form.name" type="text" placeholder="例：森田 花子" />
            <p class="err-msg" v-if="errors.name">{{ errors.name }}</p>
          </div>

          <div class="field" :class="{ error: errors.email }">
            <label>メールアドレス</label>
            <input v-model="form.email" type="email" placeholder="例：hanako@example.com" />
            <p class="err-msg" v-if="errors.email">{{ errors.email }}</p>
          </div>

          <div class="field" :class="{ error: errors.message }">
            <label>お問い合わせ内容</label>
            <textarea v-model="form.message" rows="4" placeholder="ご相談内容をご記入ください"></textarea>
            <p class="err-msg" v-if="errors.message">{{ errors.message }}</p>
          </div>

          <button class="btn btn-stamp" style="width: 100%" @click="submit">送信する</button>
        </template>

        <div class="contact-success" v-else>
          <div class="stamp">受付完了</div>
          <p style="font-weight: 700; margin-bottom: 6px;">お問い合わせを受け付けました</p>
          <p style="font-size: 13.5px; color: var(--color-ink-soft);">
            {{ form.email }} 宛に確認メールをお送りします（デモ画面のため実際には送信されません）。
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact { padding: 80px 0 96px; }
.contact-grid {
  display: grid;
  grid-template-columns: .85fr 1.15fr;
  gap: 48px;
}
.contact-card {
  background: var(--color-surface);
  border-radius: var(--radius-card);
  border: 1px solid var(--color-line);
  padding: 32px;
}
.field { margin-bottom: 18px; }
.field label { display: block; font-size: 13px; font-weight: 700; margin-bottom: 6px; }
.field input, .field textarea {
  width: 100%;
  padding: 11px 13px;
  border-radius: 8px;
  border: 1.5px solid var(--color-line);
  font-family: var(--font-body);
  font-size: 14.5px;
  background: var(--color-bg);
  transition: border-color .15s ease;
}
.field input:focus, .field textarea:focus { border-color: var(--color-ink); outline: none; }
.field.error input, .field.error textarea { border-color: var(--color-stamp); }
.field .err-msg { font-size: 12px; color: var(--color-stamp); margin-top: 5px; font-family: var(--font-mono); }

.contact-success { text-align: center; padding: 40px 20px; }
.contact-success .stamp {
  margin: 0 auto 18px;
  width: 80px;
  height: 80px;
  font-size: 14px;
  border-radius: 50%;
  border: 2.5px solid var(--color-stamp);
  color: var(--color-stamp);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-display);
  font-weight: 800;
  transform: rotate(-10deg);
}

@media (max-width: 860px) {
  .contact-grid { grid-template-columns: 1fr; }
}
</style>
