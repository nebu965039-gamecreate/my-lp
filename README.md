# まいど ― 予約管理SaaS LP（ポートフォリオ用）

個人サロン・教室・士業向けの予約管理SaaSを想定した、架空のサービスLPです。
LPコーディング案件 + Vue.jsでの軽微な機能実装、という副業の入口として一番取りやすい案件タイプを意識して作成しました。

**デモ:** `npm run dev` で起動、または `dist/` をビルドして任意の静的ホスティングに配置できます。

## 技術スタック

- Vue 3（Composition API, `<script setup>`）
- Vite
- 素のCSS（Tailwindなどは未使用。スコープ付きCSSと共通のデザイントークンのみで構成）

## この実装で見せたいポイント

実際の案件で頻出する、Vueの基本パターンを一通り含めています。

| 機能 | 使っているVueの仕組み | ファイル |
|---|---|---|
| 料金プランの月払い/年払い切り替え | `ref`、条件分岐レンダリング、算出ロジック | `PricingSection.vue` |
| FAQの開閉アコーディオン | `v-for` + 配列内オブジェクトの状態更新 | `FaqSection.vue` |
| お問い合わせフォームの入力チェック | `v-model`、フォームバリデーション、状態による画面切り替え | `ContactSection.vue` |
| ヒーローのスタンプ演出 | `onMounted` + `setTimeout`、CSSトランジション | `HeroSection.vue` |
| スクロールに合わせたセクションのフェードイン | `IntersectionObserver`とのVue連携 | `App.vue` |
| 4ステップの利用フロー | `v-for`による繰り返しレンダリング | `HowItWorksSection.vue` |

## ディレクトリ構成

```
maido-booking-lp/
├── index.html
├── package.json
├── vite.config.js
└── src/
    ├── main.js
    ├── App.vue
    ├── style.css            # デザイントークン（色・フォント等のCSS変数）
    └── components/
        ├── AppHeader.vue
        ├── HeroSection.vue
        ├── FeaturesSection.vue
        ├── HowItWorksSection.vue
        ├── PricingSection.vue
        ├── FaqSection.vue
        ├── ContactSection.vue
        └── AppFooter.vue
```

## セットアップ

```bash
npm install
npm run dev      # 開発サーバー起動
npm run build    # 本番ビルド（distフォルダに出力）
```

## 案件応募時のアピール文例

> Vue 3（Composition API）を使い、LPの実装に加えて料金トグル・FAQアコーディオン・フォーム検証などの
> インタラクティブな機能を実装しました。コンポーネント単位で責務を分割し、保守しやすい構成にしています。

---
※ これはポートフォリオ用に作成した架空サービスのデモです。実在の企業・サービスとは関係ありません。
