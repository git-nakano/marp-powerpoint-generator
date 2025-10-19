---
marp: true
theme: default
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

<!-- _class: lead -->

# SEO維持 + AI最適化
## 汎用開発工程フロー

**あらゆる業種・規模・サービスで使える**

検索流入を守りながらAI時代に対応する実践ガイド

---

## このフローの対象範囲

### 適用可能なサイトタイプ

| タイプ | 例 | 適用度 | 重点対策 |
|--------|-----|--------|---------|
| **コーポレート** | 企業HP、IR | ◎ | Organization |
| **サービス** | SaaS、アプリ | ◎ | Product/Service |
| **EC** | ネットショップ | ◎ | Product/Offer |
| **メディア** | ブログ、ニュース | ◎ | Article/FAQ |
| **ポートフォリオ** | 個人・制作会社 | ○ | Person/CreativeWork |

### 対象規模
```
スタートアップ → 中小企業 → 大企業
全規模対応（リソース別の優先順位ガイド付き）
```

---

## 本フローの目的

### 2つの目標を同時達成

```
従来のSEO（検索流入維持）
        ＋
LLMO（AI Overview/LLM引用対策）
        ↓
包括的なデジタル可視性の実現
```

**重要**: SEOとLLMOは**80%が共通要素**  
→ 置き換えではなく、進化形として実装

---

## 全体像：6つのフェーズ

| フェーズ | 期間目安 | ゴール | 優先度 |
|---------|---------|--------|--------|
| **0. 事前分析** | 3～5日 | 現状把握・課題特定 | 必須 |
| **1. 開発準備** | 2～3日 | 環境構築・設計 | 必須 |
| **2. 実装** | 5～10日 | コード開発・最適化 | 必須 |
| **3. 検証** | 2～3日 | 品質確認・テスト | 必須 |
| **4. 公開・運用** | 1日～ | デプロイ・監視開始 | 必須 |
| **5. 継続改善** | 継続 | 効果測定・改善 | 推奨 |

**合計所要時間**: 約2～4週間（初回リリース）

---

<!-- _class: lead -->

# フェーズ0
## 事前分析

---

## フェーズ0：事前分析（3～5日）

### 目的
- 既存サイトの現状把握
- 業種・サービス特性の理解
- SEO/LLMO観点での課題特定
- 改善優先度の決定

### 実施内容

#### 1. ビジネス理解（半日）
```
□ 業種・業態の確認（BtoB / BtoC / BtoG）
□ ターゲット顧客の明確化
□ 主要サービス・商品の整理
□ 競合サイトのリストアップ
```

---

## フェーズ0：業種別チェックポイント

### 業種別の重要要素

| 業種 | 重要Schema | 重要ページ | AI検索での強調点 |
|------|-----------|----------|----------------|
| **BtoB企業** | Organization | 事業内容、実績 | 専門性・信頼性 |
| **BtoC企業** | Organization, Product | サービス、価格 | わかりやすさ |
| **EC** | Product, Offer | 商品、配送 | 価格・在庫・レビュー |
| **メディア** | Article, NewsArticle | 記事、FAQ | 情報の鮮度・正確性 |
| **SaaS** | SoftwareApplication | 機能、料金 | 機能・導入事例 |
| **飲食** | Restaurant, Menu | メニュー、予約 | 営業時間・場所 |
| **医療** | MedicalBusiness | 診療科、医師 | 資格・専門性 |

---

## フェーズ0：現状調査（1～2日）

### 1. SEO現状調査

```
□ Google Search Consoleでインデックス状況確認
□ PageSpeed Insightsでパフォーマンス測定
□ Google アナリティクスで流入キーワード分析
□ 主要キーワードでの検索順位確認
□ 競合サイトのSEO状況調査
  - 構造化データ実装状況
  - ページ速度
  - コンテンツ量
```

---

## フェーズ0：現状調査（続き）

### 2. LLMO対応状況チェック

```
□ 構造化データ（JSON-LD）の有無・種類確認
□ llms.txt の実装状況
□ robots.txt のAIクローラー許可設定
□ AI検索エンジンでの引用状況確認
  - ChatGPT: 企業/サービス名で検索
  - Perplexity: 業種+地域で検索
  - Claude: 専門性の高い質問
  - Google AI Overviews: 対象クエリで検索
```

**確認方法**:
```
例1（企業）: "[貴社名]について教えて"
例2（EC）: "[商品カテゴリ] おすすめ"
例3（メディア）: "[専門分野]の最新情報"
```

---

## フェーズ0：ギャップ分析（1～2日）

### サイトタイプ別の優先度マトリクス

| 項目 | コーポレート | EC | メディア | SaaS |
|------|------------|-----|---------|------|
| JSON-LD | 高（Organization） | 高（Product） | 高（Article） | 高（Software） |
| llms.txt | 高 | 中 | 中 | 高 |
| FAQ | 中 | 高 | 低 | 高 |
| レビュー | 低 | 高 | 低 | 中 |
| 価格情報 | 低 | 高 | 低 | 高 |
| 営業時間 | 業種依存 | 中 | 低 | 低 |

**優先度**: 高＝Phase2で必須実装 / 中＝Phase5で追加 / 低＝オプション

---

## フェーズ0：リソース別戦略

### 小規模（1～2名）: ミニマム戦略

```
優先度S: 
□ Organization / Product 基本スキーマ
□ llms.txt（最小限の情報）
□ robots.txt でAI許可

優先度A:
□ メタデータ最適化
□ PageSpeed 80点以上

後回し可:
- 複雑なスキーマ
- 大量のFAQ
- 多言語対応
```

---

## フェーズ0：リソース別戦略（続き）

### 中規模（3～5名）: バランス戦略

```
優先度S:
□ 主要スキーマ2～3種類
□ llms.txt（詳細情報）
□ FAQ 10～20件

優先度A:
□ メタデータ全ページ最適化
□ PageSpeed 90点以上
□ 月次更新体制

段階的実装:
- 追加スキーマ（BreadcrumbList等）
- 多言語（英語のみ）
```

---

## フェーズ0：リソース別戦略（続き）

### 大規模（6名以上）: フル戦略

```
優先度S:
□ 全種類のスキーマ実装
□ llms.txt（網羅的情報）
□ FAQ 50件以上
□ 自動更新システム

優先度A:
□ A/Bテスト実施
□ AI引用モニタリング
□ 競合分析ダッシュボード

継続実装:
- 多言語（5言語以上）
- 動的スキーマ生成
- リアルタイム最適化
```

---

## フェーズ0：成果物

### 作成ドキュメント

1. **現状分析レポート**（A4 2～3枚）
   - SEOスコア（PageSpeed、Search Console）
   - LLMO対応度（5段階評価）
   - 競合比較
   - **業種特有の課題**

2. **改善優先度マップ**（Excel/スプレッドシート）
   - 項目、現状、目標、工数、優先度
   - **リソースに応じた実装スケジュール**

3. **タスクリスト**（次フェーズへの引継ぎ）

---

<!-- _class: lead -->

# フェーズ1
## 開発準備

---

## フェーズ1：開発準備（2～3日）

### 目的
- 開発環境の構築
- 技術スタックの決定（業種・要件に応じて）
- 設計ドキュメント作成

### 実施内容

#### 1. 環境構築（半日）
```
基本ツール:
□ Node.js インストール（v20.x推奨）
□ VSCode or 好みのエディタ
□ Git インストール・設定
```

---

## フェーズ1：技術スタック選択ガイド

### フレームワーク選択マトリクス

| フレームワーク | 適合サイト | メリット | 学習コスト |
|--------------|----------|---------|-----------|
| **Next.js** | 全般 | SEO最強、柔軟性高 | 中 |
| **Nuxt.js** | Vue好き | Vue使える | 中 |
| **Astro** | コンテンツ重視 | 超高速、簡単 | 低 |
| **WordPress** | 既存WP | プラグイン豊富 | 低 |
| **HTML/CSS** | 小規模 | シンプル | 最低 |

**推奨**: 新規ならNext.js、既存ならそのまま最適化

---

## フェーズ1：ホスティング選択ガイド

### ホスティングサービス比較

| サービス | 無料枠 | 特徴 | 推奨用途 |
|---------|-------|------|---------|
| **Cloudflare Pages** | ○ | 超高速、簡単 | 静的サイト全般 |
| **Vercel** | ○ | Next.js最適 | Next.js専用 |
| **Netlify** | ○ | 使いやすい | JAMstack |
| **GitHub Pages** | ○ | 無料、簡単 | シンプルなサイト |
| **AWS S3 + CloudFront** | △ | 柔軟性高 | 大規模・カスタム |
| **レンタルサーバー** | × | 既存契約活用 | WordPress等 |

**推奨**: 無料枠ならCloudflare Pages、既存インフラならそのまま活用

---

## フェーズ1：情報設計（1日）

### Schema.org タイプ別設計

#### 1. コーポレートサイト
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "[貴社名]",
  "description": "[事業内容の説明]",
  "url": "https://example.com",
  "foundingDate": "YYYY-MM-DD",
  "address": { ... },
  "contactPoint": { ... }
}
```

---

## フェーズ1：情報設計（続き）

#### 2. ECサイト
```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "[商品名]",
  "description": "[商品説明]",
  "image": "https://example.com/product.jpg",
  "offers": {
    "@type": "Offer",
    "price": "10000",
    "priceCurrency": "JPY",
    "availability": "https://schema.org/InStock"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5",
    "reviewCount": "120"
  }
}
```

---

## フェーズ1：情報設計（続き）

#### 3. メディア/ブログ
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[記事タイトル]",
  "author": {
    "@type": "Person",
    "name": "[著者名]"
  },
  "datePublished": "YYYY-MM-DD",
  "dateModified": "YYYY-MM-DD",
  "publisher": {
    "@type": "Organization",
    "name": "[サイト名]",
    "logo": { ... }
  }
}
```

---

## フェーズ1：情報設計（続き）

#### 4. SaaS/サービスサイト
```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "[サービス名]",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "JPY",
    "priceSpecification": {
      "@type": "UnitPriceSpecification",
      "price": "1000",
      "priceCurrency": "JPY",
      "unitText": "MONTH"
    }
  }
}
```

---

## フェーズ1：llms.txt 設計（業種別）

### コーポレートサイト向け
```
# [貴社名] - AI向け企業情報

## 基本情報
Company: [貴社名]
Founded: YYYY-MM-DD
Industry: [業種]
Employees: [従業員数]

## 事業内容
Services:
- [サービス1]
- [サービス2]
- [サービス3]

## 強み・特徴
- [強み1]
- [強み2]

## 連絡先
Website: https://example.com
Email: contact@example.com

## 更新情報
Last-Updated: YYYY-MM-DD
```

---

## フェーズ1：llms.txt 設計（続き）

### ECサイト向け
```
# [ショップ名] - AI向けショップ情報

## 基本情報
Shop Name: [ショップ名]
Category: [商品カテゴリ]
Founded: YYYY-MM-DD

## 取扱商品
Product Categories:
- [カテゴリ1]: [商品数]点
- [カテゴリ2]: [商品数]点

## 配送・支払い
Shipping: 全国配送可能（離島除く）
Payment: クレジットカード、銀行振込、代引き
Shipping Fee: [金額]円（[条件]以上で無料）

## 営業情報
Business Hours: 10:00-18:00（平日）
Phone: 000-0000-0000

## 更新情報
Last-Updated: YYYY-MM-DD
```

---

## フェーズ1：llms.txt 設計（続き）

### メディア/ブログ向け
```
# [メディア名] - AI向けメディア情報

## 基本情報
Site Name: [メディア名]
Type: [オウンドメディア/ニュースサイト等]
Founded: YYYY-MM-DD

## 専門分野
Topics:
- [トピック1]: [記事数]本
- [トピック2]: [記事数]本

## 編集方針
- 正確性を最重視
- 専門家監修
- 定期的な情報更新

## 著者情報
Writers: [ライター数]名
Experts: [専門家数]名

## 更新情報
Update Frequency: [週/日]更新
Last-Updated: YYYY-MM-DD
```

---

## フェーズ1：SEO/LLMOキーワード設計

### 業種別キーワード戦略

| 業種 | メインKW | サブKW | LLMO対象クエリ例 |
|------|---------|--------|----------------|
| **BtoB** | 企業名、サービス名 | 導入事例、業界 | "◯◯社のサービス内容は？" |
| **EC** | 商品名、カテゴリ | 価格、レビュー | "◯◯ おすすめ 通販" |
| **メディア** | トピック、ハウツー | 最新情報 | "◯◯について詳しく教えて" |
| **SaaS** | ツール名、機能 | 料金、比較 | "◯◯と△△の違いは？" |
| **地域** | 地域名+業種 | サービス内容 | "◯◯市で△△するなら" |

---

## フェーズ1：成果物

### 作成ドキュメント

1. **技術仕様書**（A4 3～5枚）
   - 技術スタック一覧（選定理由付き）
   - ディレクトリ構成
   - 命名規則
   - **業種特有の実装要件**

2. **情報設計書**（スプレッドシート）
   - ページ構成
   - JSON-LD設計（業種別）
   - メタデータ一覧
   - **llms.txt設計（業種別）**

3. **開発タスクリスト**（GitHub Issues等）

---

<!-- _class: lead -->

# フェーズ2
## 実装

---

## フェーズ2：実装（5～10日）

### 目的
- コード開発
- SEO/LLMO要素の実装
- パフォーマンス最適化

### 実装順序（推奨・業種共通）

```
Day 1-2: 基本ページ作成
Day 3-4: JSON-LD実装（業種別）
Day 5:   llms.txt/robots.txt/sitemap.xml
Day 6-7: パフォーマンス最適化
Day 8-9: レスポンシブ対応
Day 10:  バッファ（調整・修正）
```

---

## フェーズ2：実装（Day 1-2）

### 基本ページ作成（フレームワーク非依存）

#### HTMLの場合
```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>[ページタイトル] | [サイト名]</title>
  <meta name="description" content="[説明文]">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- JSON-LDをここに挿入（後述） -->
</head>
<body>
  <header>
    <nav>...</nav>
  </header>
  <main>
    <h1>[メインタイトル]</h1>
    <!-- コンテンツ -->
  </main>
  <footer>...</footer>
</body>
</html>
```

---

## フェーズ2：実装（Day 1-2 続き）

#### Next.jsの場合
```typescript
// app/layout.tsx
export const metadata: Metadata = {
  title: {
    default: '[サイト名]',
    template: '%s | [サイト名]'
  },
  description: '[サイトの説明]',
  openGraph: {
    title: '[サイト名]',
    description: '[説明]',
    url: 'https://example.com',
    siteName: '[サイト名]',
    locale: 'ja_JP',
    type: 'website',
  }
};
```

---

## フェーズ2：実装（Day 1-2 続き）

#### WordPressの場合
```php
<!-- functions.php または SEOプラグイン -->
<?php
// Yoast SEO / All in One SEO 等を使用
// または手動でメタタグ出力
function custom_meta_tags() {
  if (is_single() || is_page()) {
    echo '<meta name="description" content="' . 
         get_the_excerpt() . '">';
  }
}
add_action('wp_head', 'custom_meta_tags');
?>
```

---

## フェーズ2：実装（Day 3-4）

### JSON-LD実装（業種別）

#### コーポレートサイト
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "[貴社名]",
  "alternateName": "[略称]",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "foundingDate": "YYYY-MM-DD",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "[番地]",
    "addressLocality": "[市区町村]",
    "addressRegion": "[都道府県]",
    "postalCode": "000-0000",
    "addressCountry": "JP"
  },
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+81-00-0000-0000",
    "contactType": "customer service",
    "areaServed": "JP",
    "availableLanguage": "Japanese"
  }
}
</script>
```

---

## フェーズ2：実装（Day 3-4 続き）

#### ECサイト（商品ページ）
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "[商品名]",
  "image": "[商品画像URL]",
  "description": "[商品説明]",
  "sku": "[商品コード]",
  "brand": {
    "@type": "Brand",
    "name": "[ブランド名]"
  },
  "offers": {
    "@type": "Offer",
    "url": "[商品ページURL]",
    "priceCurrency": "JPY",
    "price": "10000",
    "priceValidUntil": "YYYY-MM-DD",
    "availability": "https://schema.org/InStock",
    "itemCondition": "https://schema.org/NewCondition"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5",
    "reviewCount": "89"
  }
}
</script>
```

---

## フェーズ2：実装（Day 3-4 続き）

#### メディア/ブログ（記事ページ）
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[記事タイトル]",
  "description": "[記事概要]",
  "image": "[アイキャッチ画像URL]",
  "author": {
    "@type": "Person",
    "name": "[著者名]",
    "url": "[著者ページURL]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "[サイト名]",
    "logo": {
      "@type": "ImageObject",
      "url": "[ロゴURL]"
    }
  },
  "datePublished": "YYYY-MM-DD",
  "dateModified": "YYYY-MM-DD"
}
</script>
```

---

## フェーズ2：実装（Day 3-4 続き）

#### SaaS/サービスサイト
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "[サービス名]",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "description": "[サービス説明]",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "JPY"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "reviewCount": "250"
  }
}
</script>
```

---

## フェーズ2：実装（Day 5）

### llms.txt 作成（配置場所）

#### 静的サイト・Next.js
```
プロジェクトルート/
  public/
    llms.txt  ← ここに配置
```

#### WordPress
```
wp-content/
  themes/
    your-theme/
      llms.txt  ← ここに配置

または

Webサーバーのルート/
  llms.txt  ← ここに配置
```

**重要**: https://example.com/llms.txt でアクセスできること

---

## フェーズ2：実装（Day 5 続き）

### robots.txt 設定（業種共通）

```
# 基本設定
User-agent: *
Allow: /

# AI Crawlers（明示的に許可）
User-agent: ChatGPT-User
Allow: /

User-agent: GPTBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: Google-Extended
Allow: /

# Anthropic AI
User-agent: anthropic-ai
Allow: /

# Sitemap
Sitemap: https://example.com/sitemap.xml

# 除外パス（サイトに応じて調整）
Disallow: /admin/
Disallow: /cart/
Disallow: /checkout/
Disallow: /my-account/
Disallow: /wp-admin/
Disallow: /_next/
```

---

## フェーズ2：実装（Day 5 続き）

### sitemap.xml 生成方法

#### Next.js（手動生成）
```typescript
// app/sitemap.ts
import { MetadataRoute } from 'next'

export default function sitemap(): MetadataRoute.Sitemap {
  return [
    {
      url: 'https://example.com',
      lastModified: new Date(),
      changeFrequency: 'weekly',
      priority: 1,
    },
    {
      url: 'https://example.com/about',
      lastModified: new Date(),
      changeFrequency: 'monthly',
      priority: 0.8,
    },
    // 各ページを追加
  ]
}
```

---

## フェーズ2：実装（Day 5 続き）

#### WordPress（プラグイン使用）
```
推奨プラグイン:
- Yoast SEO
- All in One SEO
- Google XML Sitemaps

設定方法:
1. プラグインインストール
2. 設定画面で「Sitemap生成」有効化
3. robots.txtにSitemap行を追加
```

#### 静的HTML（オンラインジェネレーター）
```
ツール:
- XML-Sitemaps.com
- Screaming Frog SEO Spider（無料版500ページまで）

手順:
1. ツールでサイトをクロール
2. sitemap.xml生成
3. ルートディレクトリに配置
```

---

## フェーズ2：実装（Day 6-7）

### パフォーマンス最適化（業種共通）

#### 1. 画像最適化
```
□ WebP形式に変換（PNG/JPEGより30%軽量）
□ 適切なサイズにリサイズ
□ 遅延読み込み（lazy loading）実装
□ Next.js Image / imgタグのloading属性
```

**ツール**:
- Squoosh（https://squoosh.app/）
- TinyPNG（https://tinypng.com/）
- ImageOptim（Mac）

---

## フェーズ2：実装（Day 6-7 続き）

#### 2. フォント最適化
```
□ Google Fontsならfont-display: swapを使用
□ サブセット化（必要な文字のみ）
□ preconnectで先読み
```

**HTML例**:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&display=swap" rel="stylesheet">
```

---

## フェーズ2：実装（Day 6-7 続き）

#### 3. CSS/JS最適化
```
□ CSSミニファイ（圧縮）
□ JSミニファイ
□ 不要なコード削除
□ Critical CSS（ファーストビュー用CSS）をインライン化
```

**ツール**:
- cssnano
- Terser
- PurgeCSS（未使用CSS削除）

---

## フェーズ2：実装（Day 8-9）

### レスポンシブ対応（業種共通）

#### メディアクエリの基本
```css
/* モバイルファースト */
.container {
  padding: 16px;
  font-size: 14px;
}

/* タブレット（768px以上） */
@media (min-width: 768px) {
  .container {
    padding: 32px;
    font-size: 16px;
  }
}

/* デスクトップ（1024px以上） */
@media (min-width: 1024px) {
  .container {
    padding: 64px;
    font-size: 18px;
  }
}
```

---

## フェーズ2：チェックリスト

### 実装完了確認（業種共通）

```
基本実装
□ 全ページが正しく表示される
□ ナビゲーションが機能する
□ リンクが正しく動作する

SEO実装
□ 各ページにtitle/description設定
□ Open Graphタグ実装
□ JSON-LD実装（業種に応じた種類）

LLMO実装
□ llms.txt 配置（業種別内容）
□ robots.txt でAIクローラー許可
□ sitemap.xml 生成

パフォーマンス
□ 画像最適化（WebP、lazy loading）
□ フォント最適化
□ CSS/JSミニファイ

レスポンシブ
□ モバイル表示確認
□ タブレット表示確認
□ デスクトップ表示確認
```

---

<!-- _class: lead -->

# フェーズ3
## 検証

---

## フェーズ3：検証（2～3日）

### 目的
- 実装品質の確認
- SEO/LLMO要素の動作検証
- 問題点の早期発見・修正

### 検証カテゴリ（8項目・業種共通）

```
1. 基本設定
2. JSON-LD構造化データ
3. llms.txt
4. robots.txt / sitemap.xml
5. HTMLメタデータ
6. パフォーマンス
7. クローラビリティ
8. レスポンシブ対応
```

---

## フェーズ3：検証ツール一覧

### 使用ツール（すべて無料）

| ツール | 用途 | URL |
|--------|------|-----|
| **Rich Results Test** | JSON-LD検証 | https://search.google.com/test/rich-results |
| **PageSpeed Insights** | パフォーマンス | https://pagespeed.web.dev/ |
| **Schema Validator** | 構造化データ | https://validator.schema.org/ |
| **Mobile-Friendly Test** | モバイル対応 | https://search.google.com/test/mobile-friendly |
| **ブラウザ開発者ツール** | 総合確認 | F12キー |

---

## フェーズ3：検証（Day 1）

### 1. ローカル/ステージング環境での検証

```
□ サイトが正しく表示される
□ 全ページ遷移が正常
□ コンソールエラーなし
□ llms.txt が表示される（/llms.txt）
□ robots.txt が表示される（/robots.txt）
□ sitemap.xml が表示される（/sitemap.xml）
```

**確認コマンド**:
```bash
# リンク切れチェック
curl -I https://example.com/llms.txt
# → 200 OK が返ること
```

---

## フェーズ3：検証（Day 2）

### 2. JSON-LD検証（業種別）

#### Google Rich Results Test
```
1. https://search.google.com/test/rich-results
2. URLまたはコードを入力
3. 「URLをテスト」クリック
```

**期待結果（業種別）**:
```
コーポレート: Organization ✅
EC: Product, Offer ✅
メディア: Article ✅
SaaS: SoftwareApplication ✅

エラー: 0件
警告: 0～2件（許容範囲）
```

---

## フェーズ3：検証（Day 2 続き）

### 3. パフォーマンス検証

#### PageSpeed Insights
```
https://pagespeed.web.dev/

期待スコア（業種共通）:
Performance:      90+ （最重要）
Accessibility:    90+
Best Practices:   90+
SEO:              90+
```

**業種別の注意点**:
- **EC**: 商品画像が多いので80点以上でもOK
- **メディア**: 記事内画像の最適化が重要
- **コーポレート**: 90点以上を目指す

---

## フェーズ3：検証（Day 3）

### 4. AI検索エンジンでの確認（業種別）

#### コーポレートサイト
```
ChatGPT:
「[貴社名]について教えて」
「[貴社名]のサービス内容は？」

期待: 企業情報、サービス内容が正確に回答される
```

#### ECサイト
```
Perplexity:
「[商品カテゴリ] おすすめ 通販」
「[ブランド名] 評判」

期待: 商品が引用される、価格情報が正確
```

---

## フェーズ3：検証（Day 3 続き）

#### メディア/ブログ
```
ChatGPT:
「[専門分野]の最新情報を教えて」
「[トピック]について詳しく」

期待: 記事が引用される、情報が正確
```

#### SaaS
```
Claude:
「[サービス名]の機能を教えて」
「[サービス名]と[競合]の違いは？」

期待: 機能説明が正確、比較情報が引用される
```

**注意**: AI反映には数週間～数ヶ月かかる場合あり

---

## フェーズ3：検証チェックシート

### 総合チェックリスト（業種共通）

| カテゴリ | 項目 | 合格基準 |
|---------|------|---------|
| **基本** | サイト表示 | ✅ 全ページ正常 |
| **基本** | HTTPS | ✅ 鍵アイコン表示 |
| **JSON-LD** | スキーマ実装 | ✅ 業種適合 |
| **JSON-LD** | 構文エラー | ✅ 0件 |
| **llms.txt** | ファイル存在 | ✅ 200 OK |
| **llms.txt** | 内容適切 | ✅ 業種別情報 |
| **robots.txt** | AI許可 | ✅ 全AIクローラー |
| **sitemap** | 生成成功 | ✅ 全URL含む |
| **パフォーマンス** | PageSpeed | ✅ 90点以上 |
| **レスポンシブ** | モバイル | ✅ Mobile-Friendly |

---

## フェーズ3：不具合対応（業種別）

### よくある問題と解決策

| 問題 | 業種 | 原因 | 解決策 |
|------|------|------|--------|
| JSON-LDエラー | 全般 | 構文ミス | JSONバリデーター使用 |
| 商品価格が表示されない | EC | Offer不足 | price, availability追加 |
| 記事が引用されない | メディア | datePublished欠落 | 公開日追加 |
| サービス情報不正確 | SaaS | llms.txt不十分 | 機能詳細を追記 |
| 画像が重い | 全般 | 未最適化 | WebP変換、圧縮 |

---

<!-- _class: lead -->

# フェーズ4
## 公開・運用

---

## フェーズ4：公開・運用（1日～）

### 目的
- サイトの公開
- 初期監視設定
- 運用体制の確立

### 実施内容（ホスティング別）

```
Day 1: デプロイ実行
Day 1: Google Search Console登録
Day 1: Google Analytics設定
Day 1: 初回動作確認
Day 2～7: 初期監視（1週間）
```

---

## フェーズ4：デプロイ方法（ホスティング別）

### 1. Cloudflare Pages

```
1. https://dash.cloudflare.com/ ログイン
2. Workers & Pages → Create application
3. Gitリポジトリ連携
4. ビルド設定:
   - Framework: Next.js / Astro等
   - Build command: npm run build
   - Output directory: out / dist
5. Deploy クリック
```

---

## フェーズ4：デプロイ方法（続き）

### 2. Vercel

```
1. https://vercel.com/ ログイン
2. New Project
3. Gitリポジトリ選択
4. 自動でフレームワーク検出
5. Deploy クリック
```

### 3. Netlify

```
1. https://www.netlify.com/ ログイン
2. New site from Git
3. リポジトリ選択
4. Build settings設定
5. Deploy site クリック
```

---

## フェーズ4：デプロイ方法（続き）

### 4. WordPress（既存サーバー）

```
1. FTPまたはcPanelでファイルアップロード
   - llms.txt → ルートディレクトリ
   - robots.txt → ルートディレクトリ

2. プラグインでJSON-LD実装
   - Schema Pro
   - WP SEO Structured Data Schema

3. キャッシュクリア
   - WP Super Cache
   - W3 Total Cache
```

---

## フェーズ4：初期設定（Search Console）

### Google Search Console 登録

```
1. https://search.google.com/search-console
2. プロパティを追加
3. URLプレフィックス方式で公開URL入力
4. 所有権確認
   - HTMLファイルアップロード
   - DNSレコード
   - Google Analytics連携
5. サイトマップ送信
   - sitemap.xml のURL入力
```

**確認ポイント**:
```
□ サイトマップが「成功」ステータス
□ インデックス登録が開始される（24時間以内）
```

---

## フェーズ4：初期設定（Analytics）

### Google Analytics 4 設定

```
1. https://analytics.google.com/ アクセス
2. 管理 → プロパティを作成
3. プロパティ名: [サイト名]
4. データストリーム → ウェブ
5. 公開URLを入力
6. 測定ID（G-XXXXXXXXXX）をコピー
7. サイトにトラッキングコード設置
```

---

## フェーズ4：初期設定（Analytics続き）

### トラッキングコード設置方法

#### HTML
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

#### Next.js
```typescript
// app/layout.tsx
import Script from 'next/script'

export default function RootLayout() {
  return (
    <html>
      <body>
        <Script src={`https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX`} />
        <Script id="google-analytics">
          {`
            window.dataLayer = window.dataLayer || [];
            function gtag(){dataLayer.push(arguments);}
            gtag('js', new Date());
            gtag('config', 'G-XXXXXXXXXX');
          `}
        </Script>
        {children}
      </body>
    </html>
  )
}
```

---

## フェーズ4：初期設定（Analytics続き）

#### WordPress
```
プラグイン使用（推奨）:
- Site Kit by Google
- GA Google Analytics
- MonsterInsights

手動設置:
テーマの header.php に
上記HTMLコードを貼り付け
```

---

## フェーズ4：監視設定（1週間）

### 毎日確認項目

```
Day 1-7:
□ サイトが正常に表示されるか
□ エラーログの確認（ホスティング管理画面）
□ Search Consoleのクロールエラー
□ PageSpeed Insightsスコア維持
□ Analytics でアクセス計測開始確認

1週間後:
□ Google検索でインデックス確認
  検索: site:example.com
□ JSON-LDがGoogleに認識されたか
  Search Console → 拡張 → 構造化データ
```

---

<!-- _class: lead -->

# フェーズ5
## 継続改善

---

## フェーズ5：継続改善（継続的）

### 目的
- SEO/LLMO効果の測定
- データに基づく改善
- 競合分析・対策

### 測定指標（KPI）業種別

| 業種 | 主要KPI | 測定方法 | 目標値 |
|------|---------|---------|--------|
| **コーポレート** | オーガニック流入 | GA4 | 前月比+10% |
| **EC** | CV率、売上 | GA4, ECツール | CV率3%以上 |
| **メディア** | PV、記事引用数 | GA4, 手動確認 | PV月+15% |
| **SaaS** | リード獲得数 | GA4, CRM | 月50件以上 |

---

## フェーズ5：月次メンテナンス

### 毎月実施タスク（業種共通）

#### 第1週：データ収集
```
□ GA4で前月の流入データダウンロード
□ Search Consoleで検索パフォーマンス確認
□ AI検索エンジンで企業/サービス名検索
  - ChatGPT
  - Perplexity
  - Claude
  - Google AI Overviews
□ 競合サイトの変化確認
```

---

## フェーズ5：月次メンテナンス（続き）

#### 第2週：コンテンツ更新（業種別）

**コーポレート**:
```
□ llms.txt の Last-Updated 更新
□ 新サービス・ニュースがあれば追加
□ JSON-LDの情報更新（住所変更等）
□ ブログ記事追加（月1～2本）
```

**EC**:
```
□ 新商品の構造化データ追加
□ 在庫状況の更新
□ セール情報の反映
□ レビューの構造化データ追加
```

---

## フェーズ5：月次メンテナンス（続き）

**メディア**:
```
□ 記事の情報鮮度確認・更新
□ FAQの追加（月5～10件）
□ 古い記事のリライト
□ 新着記事の構造化データ実装
```

**SaaS**:
```
□ 機能追加の反映
□ 料金改定の更新
□ ユーザーレビューの追加
□ 事例記事の追加
```

---

## フェーズ5：月次メンテナンス（続き）

#### 第3週：技術チェック（業種共通）
```
□ PageSpeed Insights再測定
□ リンク切れチェック
□ セキュリティアップデート確認
□ フレームワークバージョンアップ検討
□ ホスティング使用量確認
```

---

## フェーズ5：四半期レビュー（3ヶ月ごと）

### 詳細分析（業種共通）

```
□ SEO/LLMO効果の定量評価
  - オーガニック流入推移
  - 検索順位の変動
  - AI引用実績
  - コンバージョン率

□ 競合サイトとの比較
  - 構造化データ実装状況
  - コンテンツ量・質
  - パフォーマンススコア

□ 新規施策の立案
  - 不足している要素の追加
  - 業界トレンドへの対応

□ 技術スタックの見直し
```

---

## フェーズ5：AI検索エンジン確認方法（業種別）

### コーポレートサイト

**ChatGPT**:
```
質問: "[貴社名]について教えて"
期待: 企業概要、サービス、所在地が正確
```

**Perplexity**:
```
質問: "[業種] [地域] おすすめ企業"
期待: 検索結果に自社が含まれる
```

---

## フェーズ5：AI検索エンジン確認方法（続き）

### ECサイト

**ChatGPT**:
```
質問: "[商品カテゴリ] おすすめを教えて"
期待: 自社商品が候補に挙がる
```

**Perplexity**:
```
質問: "[商品名] 最安値"
期待: 価格情報が正確に表示される
```

---

## フェーズ5：AI検索エンジン確認方法（続き）

### メディア/ブログ

**ChatGPT**:
```
質問: "[専門分野]について詳しく教えて"
期待: 記事が引用元として表示される
```

**Claude**:
```
質問: "[トピック]の最新情報"
期待: 最新記事が参照される
```

---

## フェーズ5：AI検索エンジン確認方法（続き）

### SaaS

**ChatGPT**:
```
質問: "[サービス名]の機能を教えて"
期待: 主要機能、料金が正確
```

**Perplexity**:
```
質問: "[サービス名] vs [競合]"
期待: 比較情報で自社が引用される
```

---

## フェーズ5：改善サイクル（PDCA）

```
Plan: KPI設定（業種別の目標値）
  ↓
Do: 施策実行（コンテンツ追加、技術改善）
  ↓
Check: 効果測定（GA4、Search Console、AI検索）
  ↓
Action: 改善実施（効果ある施策の横展開）
  ↓
Plan: ...（継続）
```

### 具体例（業種別）

**EC**: AI引用を月3回→月10回に増やす
→ 商品レビュー・FAQ追加 → 3ヶ月後確認

**メディア**: 特定キーワードでTOP3入り
→ 記事リライト、内部リンク強化 → 2ヶ月後確認

---

<!-- _class: lead -->

# まとめ

---

## 開発工程フロー まとめ

### 全体スケジュール（再掲）

| フェーズ | 期間 | 重要ポイント |
|---------|------|-------------|
| 0. 事前分析 | 3～5日 | **業種特性の理解** |
| 1. 開発準備 | 2～3日 | **技術スタック選定** |
| 2. 実装 | 5～10日 | **業種別Schema実装** |
| 3. 検証 | 2～3日 | 8項目の品質チェック |
| 4. 公開・運用 | 1日～ | **ホスティング別デプロイ** |
| 5. 継続改善 | 継続 | **業種別KPI測定** |

**合計**: 約2～4週間で初回リリース

---

## ✅ 成功のための5つの原則

### 1. 業種に応じた最適化
```
コーポレート: Organization中心
EC: Product + Offer + Review
メディア: Article + FAQ
SaaS: SoftwareApplication + FAQ
```

### 2. リソースに応じた優先順位
```
小規模: ミニマム戦略（必須のみ）
中規模: バランス戦略（段階実装）
大規模: フル戦略（網羅的実装）
```

---

## ✅ 成功のための5つの原則（続き）

### 3. 技術スタックは柔軟に
```
新規: Next.js / Astro（高速、SEO強い）
既存: WordPress等をそのまま最適化
重要: フレームワークよりコンテンツ品質
```

### 4. SEOとLLMOは共存
```
❌ SEOを捨ててLLMOに全振り
✅ SEOの80%を維持しつつLLMO追加
```

### 5. 長期視点で取り組む
```
効果が出るまで: 2～6ヶ月
継続的な改善が必須
```

---

## 期待される効果（業種別）

### コーポレートサイト
- オーガニック流入: +15～30%
- AI引用回数: 月3～10回
- ブランド認知: +20%

### ECサイト
- 商品ページ流入: +25～40%
- 購入CV率: +0.5～1%
- AI経由購入: 全体の3～5%

### メディア/ブログ
- 記事PV: +30～50%
- AI引用率: +750%（構造化データ実装時）
- 滞在時間: +20%

### SaaS
- リード獲得: +20～35%
- AI経由問い合わせ: 月5～15件
- 認知度向上: +25%

---

## 推奨ツール一覧（業種共通）

| カテゴリ | ツール | 用途 | 料金 |
|---------|--------|------|------|
| **開発** | VSCode | コードエディタ | 無料 |
| **検証** | Rich Results Test | JSON-LD確認 | 無料 |
| **検証** | PageSpeed Insights | パフォーマンス | 無料 |
| **分析** | Google Analytics 4 | アクセス解析 | 無料 |
| **分析** | Search Console | SEO分析 | 無料 |
| **画像** | Squoosh | 画像圧縮 | 無料 |
| **監視** | Uptime Robot | 稼働監視 | 無料 |

---

## 参考資料

### プロジェクト内ドキュメント
- **LLMO最適化仕様書.pdf**: 理論・概念
- **LLMO技術対策ガイド.pdf**: 実装詳細
- **Next.js Cloudflare LLMO guide.md**: 開発マニュアル
- **LLMO verification manual.md**: 検証手順

### 外部リソース
- Schema.org: https://schema.org/
- Google Search Central: https://developers.google.com/search
- Web.dev: https://web.dev/

---

## 次のステップ

### 今すぐ始める3ステップ

```
1. フェーズ0の現状分析から開始
   - 自社の業種・規模を確認
   - 既存サイトの状況調査

2. 業種別チェックリストを活用
   - 必要なSchemaタイプを確認
   - llms.txtの内容を設計

3. リソースに応じた戦略を選択
   - 小規模 / 中規模 / 大規模
   - 優先度に沿って実装
```

---

## 次のステップ（続き）

### さらに学びたい

**業種別の深堀り**:
- EC: 商品レビュー構造化（Review Schema）
- メディア: FAQ最適化（FAQPage Schema）
- 全業種: パンくずリスト（BreadcrumbList）

**技術的な深堀り**:
- E-E-A-T強化施策
- Core Web Vitals最適化
- 多言語対応（hreflang実装）

**運用の深堀り**:
- AI引用モニタリング自動化
- 競合分析ダッシュボード構築
- A/Bテスト実施

---

## よくある質問（FAQ）

**Q1: WordPress でも実装できますか？**
A: はい。プラグイン（Schema Pro等）で実装可能です。

**Q2: 小規模サイトでも効果ありますか？**
A: あります。ミニマム戦略で必須項目のみ実装してください。

**Q3: どのくらいで効果が出ますか？**
A: 通常2～6ヶ月。継続的な改善が重要です。

**Q4: 既存サイトでも対応できますか？**
A: できます。フェーズ0で現状分析から始めてください。

**Q5: 複数のSchemaタイプを使えますか？**
A: 使えます。同一ページに複数のJSON-LD設置可能です。