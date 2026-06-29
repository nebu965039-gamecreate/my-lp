# まいど ― 予約管理SaaS ランディングページ

個人サロン・教室・士業向けの予約管理SaaSを想定した、架空サービスのランディングページです。
Vue 3（Composition API）を使用し、LPのコーディングに加えて、料金プランの切り替えやFAQの開閉、入力チェック付きフォームなどのインタラクティブな機能を実装しています。

## 主な機能

- 料金プランの月払い/年払い切り替え
- FAQのアコーディオン開閉
- 入力チェック付きのお問い合わせフォーム
- スクロールに連動したセクションのフェードイン表示
- モバイル〜デスクトップのレスポンシブ対応

## 技術スタック

- Vue 3（Composition API, `<script setup>`）
- Vite
- CSS（フレームワーク不使用。CSS変数によるデザイントークンで色・フォントを管理）

## セットアップ

```bash
npm install
npm run dev      # 開発サーバーを起動
npm run build    # 本番ビルド（distフォルダに出力）
```

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

## ライセンス

個人のポートフォリオ用プロジェクトです。

---
※ 本プロジェクトはデモ用に作成した架空サービスのLPです。実在の企業・サービスとは関係ありません。