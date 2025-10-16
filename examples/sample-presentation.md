---
marp: true
theme: default
paginate: true
footer: '© 2025 LLMO-projects
---

<!-- _class: lead -->

# LLMO最適化仕様書
## 既存Webサイトの LLM最適化開発ガイド

**対象：** 10ページ以内の規模サイト  
**技術：** WordPress / 静的HTML / React（SPA）  
**期間：** 1-2週間  

**Version:** 1.0  
**Date:** 2025-10

---

## 目次

1. **プロジェクト概要** - LLMO基礎・アーキテクチャ
2. **Layer 1: Crawler Control** - robots.txt / llms.txt
3. **Layer 2: Discoverability** - Sitemap / JSON-LD
4. **Layer 3: Content Optimization** - FAQ / 構造改善
5. **Layer 4: Monitoring** - テスト / KPI測定
6. **実装フロー** - スケジュール・チェックリスト

---

<!-- _class: chapter -->

# 第1章
## プロジェクト概要

---

## 1-1. LLMO

**LLMO = LLM Optimization（LLM最適化）**

従来のSEOに加え、ChatGPT・Perplexity等のAI検索エンジンでの**発見可能性・引用精度**を向上させる技術対策。

### 主な効果
- ✅ AI検索での言及率向上（ブランド認知）
- ✅ 引用時の情報精度改善（誤情報防止）
- ✅ 競合比較時の優位性確保

### 2025年のトレンド
- 2028年までに米国成人3,600万人がAI検索を利用予測
- RAG（リアルタイム検索）が静的学習を上回る（49%成長 Q4 2024-Q1 2025）

---

## 1-2. 4層アーキテクチャ

```
┌─────────────────────────────────┐
│ Layer 4: Monitoring & KPIs      │ ← 効果測定
│ 　(AI検索テスト・改善サイクル) 　　│
├─────────────────────────────────┤
│ Layer 3: Content Optimization   │ ← コンテンツ最適化
│ 　(FAQ・見出し・メタ情報)         │
├─────────────────────────────────┤
│ Layer 2: Discoverability        │ ← 発見可能性
│ 　(Sitemap・JSON-LD・構造化)     │
├─────────────────────────────────┤
│ Layer 1: Crawler Control        │ ← クローラー制御
│　 (robots.txt・llms.txt)     　　│
└─────────────────────────────────┘
```

**実装順序：** Layer 1（下）から順に実装

---

## 1-3. 実装スコープ・スケジュール

### 対象サイト条件
- ページ数：10ページ以内
- 技術スタック：WordPress / 静的HTML / React（SPA）
- 更新頻度：週次〜月次

### スケジュール（全2週間）
| Week | Phase | 工数 |
|------|-------|------|
| Week 1 | Layer 1 + Layer 2 | 3-4日 |
| Week 2 | Layer 3 + Layer 4 | 3-4日 |
| Week 3 | 検証・改善 | 1-2日 |

**完了定義：** 全4層の実装完了 + ChatGPT/Perplexityテスト合格

---

## 1-4. 技術スタック別対応表

| 項目 | WordPress | 静的HTML | React (SPA) |
|------|-----------|----------|-------------|
| **robots.txt** | ✅ ルート配置 | ✅ ルート配置 | ✅ public/配置 |
| **llms.txt** | ✅ ルート配置 | ✅ ルート配置 | ✅ public/配置 |
| **Sitemap** | 🔌 プラグイン | 📝 手動生成 | ⚙️ ビルド時生成 |
| **JSON-LD** | 🔌 functions.php | 📝 head内記述 | ⚙️ Helmet使用 |
| **FAQ実装** | 🔌 ブロック追加 | 📝 HTML直接編集 | ⚙️ コンポーネント化 |

**凡例：** ✅=共通、🔌=プラグイン/関数、📝=手動、⚙️=自動化可能

---

<!-- _class: chapter -->

# 第2章
## Layer 1: Crawler Control
### robots.txt / llms.txt

---

## 2-1. robots.txt 仕様

### 目的
AI検索クローラーに対してサイトの巡回ルールを明示。

### 必須設定項目
1. **AI検索クローラーの許可**（User-agent指定）
2. **管理画面・非公開ページの除外**
3. **Sitemapの場所を明示**

### 配置場所
- すべての技術スタック共通
- ドメインルート（例：`https://example.com/robots.txt`）

---

## 2-2. robots.txt 実装例

```txt
# AI検索クローラーの許可
User-agent: GPTBot
Allow: /

User-agent: ChatGPT-User
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: anthropic-ai
Allow: /

# 管理画面・非公開ページの除外
User-agent: *
Disallow: /wp-admin/
Disallow: /admin/
Disallow: /private/
Disallow: /draft/

# Sitemapの場所
Sitemap: https://example.com/sitemap.xml

```

---

## 2-3. llms.txt 仕様

### 目的
AI検索エンジン向けに**サイト概要・主要コンテンツ**を平文で提供。

### 記載内容
1. **サイト概要**（1-2文）
2. **主要セクション**（3-5項目）
3. **推奨リンク**（重要ページ5-10個）

### フォーマット
- Markdown形式（見出し・リストOK）
- 300-800文字程度
- 英語推奨（日本語可）

---

## 2-4. llms.txt 実装例

```markdown
# About Our Site
This site provides [業界/サービス名] solutions for [ターゲット].
We specialize in [専門分野] with over [年数] years of experience.

## Key Sections
- Products: Comprehensive product lineup and specifications
- Services: Custom solutions and support services
- Resources: Technical guides, whitepapers, and case studies
- Company: Our mission, team, and contact information

## Important Pages
- Homepage: https://example.com/
- Product Catalog: https://example.com/products/
- FAQ: https://example.com/faq/
- Contact: https://example.com/contact/
- Blog: https://example.com/blog/

```
**配置場所：** `https://example.com/llms.txt`（ルート直下）

---

## 2-5. AI検索クローラー一覧

### 2025年時点の主要クローラー

| クローラー名 | User-agent | サービス |
|-------------|------------|----------|
| GPTBot | `GPTBot` | ChatGPT検索 |
| ChatGPT-User | `ChatGPT-User` | ChatGPT引用 |
| PerplexityBot | `PerplexityBot` | Perplexity |
| ClaudeBot | `ClaudeBot` | Claude |
| anthropic-ai | `anthropic-ai` | Anthropic |
| Google-Extended | `Google-Extended` | Gemini |
| Bytespider | `Bytespider` | TikTok/ByteDance |

**要検証：** 新規クローラーは月次で追加される可能性あり

---

## 2-6. 検証方法
### 手順1：ファイル配置確認
```bash
# curlで確認（ステータス200を確認）
curl -I https://example.com/robots.txt
curl -I https://example.com/llms.txt
```
### 手順2：構文チェック
- robots.txt: [Google Robots Testing Tool](https://www.google.com/webmasters/tools/robots-testing-tool)
- llms.txt: テキストエディタで目視確認（Markdown表示）
### 手順3：クローラー動作確認
```bash
# User-agentを指定してアクセステスト
curl -A "GPTBot" https://example.com/
```

---

## 2-7. トラブルシューティング

### よくあるエラー

| 症状 | 原因 | 解決策 |
|------|------|--------|
| 404エラー | ファイル配置ミス | ルート直下に配置確認 |
| 文字化け | UTF-8以外 | UTF-8エンコード保存 |
| 改行コード | CRLF/LF混在 | LF統一（Unix形式） |
| キャッシュ残存 | CDN/ブラウザ | キャッシュクリア・強制再読込 |

### WordPress特有の注意
- プラグイン（Yoast SEO等）がrobots.txtを自動生成する場合あり
- `設定 > 表示設定` で「検索エンジンがサイトをインデックスしないようにする」がOFFか確認

---

## 2-8. Layer 1 完了チェックリスト

### 実装確認
- [ ] robots.txt ファイル配置完了（ルート直下）
- [ ] AI検索クローラー5種以上を許可設定
- [ ] 管理画面・非公開ページを除外設定
- [ ] Sitemap URLを記載
- [ ] llms.txt ファイル配置完了（ルート直下）
- [ ] サイト概要・主要セクション・推奨リンクを記載

### 検証確認
- [ ] ブラウザで両ファイルにアクセス可能（200 OK）
- [ ] curl -A "GPTBot" でアクセス成功
- [ ] UTF-8エンコード・LF改行確認

**完了条件：** すべて☑️でLayer 2へ進む

---

<!-- _class: chapter -->

# 第3章
## Layer 2: Discoverability
### Sitemap / JSON-LD

---

## 3-1. Sitemap XML 仕様

### 目的
全ページのURL・更新日・優先度をクローラーに通知。

### 必須要素
```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://example.com/page/</loc>        <!-- URL -->
    <lastmod>2025-10-15</lastmod>               <!-- 最終更新日 -->
    <changefreq>weekly</changefreq>             <!-- 更新頻度 -->
    <priority>0.8</priority>                    <!-- 優先度(0.0-1.0) -->
  </url>
</urlset>

```

---

### 優先度設定の目安
- `1.0` - トップページ

- `0.8` - 主要カテゴリ・商品ページ

- `0.5` - 一般コンテンツ

- `0.3` - アーカイブ・タグページ

---

## 3-2. Sitemap 実装：WordPress版

### 方法1：プラグイン使用（推奨）
```php
// Yoast SEO / Rank Math 等のプラグインで自動生成

// ダッシュボード > SEO > 一般 > 機能 > XMLサイトマップ ON
```
---

### 方法2：手動実装
```php
// functions.php に追記
function generate_custom_sitemap() {
    $posts = get_posts(['numberposts' => -1, 'post_status' => 'publish']);
    
    header('Content-Type: application/xml; charset=utf-8');
    echo '<?xml version="1.0" encoding="UTF-8"?>';
    echo '<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">';
    
    // トップページ
    echo '<url>';
    echo '<loc>' . home_url() . '</loc>';
    echo '<lastmod>' . date('Y-m-d') . '</lastmod>';
    echo '<changefreq>daily</changefreq>';
    echo '<priority>1.0</priority>';
    echo '</url>';
```

---

```php
    // 各投稿
    foreach ($posts as $post) {
        echo '<url>';
        echo '<loc>' . get_permalink($post) . '</loc>';
        echo '<lastmod>' . get_the_modified_date('Y-m-d', $post) . '</lastmod>';
        echo '<changefreq>weekly</changefreq>';
        echo '<priority>0.8</priority>';
        echo '</url>';
    }
    
    echo '</urlset>';
    exit;
}
add_action('init', function() {
    if ($_SERVER['REQUEST_URI'] === '/sitemap.xml') {
        generate_custom_sitemap();
    }
});
```

---

## 3-3. Sitemap 実装：静的HTML版

### 手動作成テンプレート
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  
  <!-- トップページ -->
  <url>
    <loc>https://example.com/</loc>
    <lastmod>2025-10-15</lastmod>
    <changefreq>daily</changefreq>
    <priority>1.0</priority>
  </url>
```
  
---

```xml
  <!-- 各ページ（10ページ分を列挙） -->
  <url>
    <loc>https://example.com/about/</loc>
    <lastmod>2025-10-10</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  
  <url>
    <loc>https://example.com/services/</loc>
    <lastmod>2025-10-12</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.8</priority>
  </url>
  
  <!-- ... 残り7ページも同様に記述 -->
  
</urlset>
```

**保存先：** `sitemap.xml`（ルート直下）

---

## 3-4. Sitemap 実装：React版

### ビルド時自動生成（Next.js例）
```javascript
// scripts/generate-sitemap.js
const fs = require('fs');
const globby = require('globby');
(async () => {const pages = await globby([
    'src/pages/**/*.jsx',
    '!src/pages/_*.jsx',
    '!src/pages/api',
  ]);
  const sitemap = `<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
${pages
  .map((page) => {
    const path = page
      .replace('src/pages', '')
      .replace('.jsx', '')
      .replace('/index', '');
    const route = path === '' ? '' : path;

```
---

```javascript
    return `  <url>
    <loc>https://example.com${route}</loc>
    <lastmod>${new Date().toISOString().split('T')[0]}</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.8</priority>
  </url>`;
  })
  .join('\n')}
</urlset>`;

  fs.writeFileSync('public/sitemap.xml', sitemap);
})();

```

**package.json に追加：**
```json
"scripts": {
  "build": "npm run generate-sitemap && next build",
  "generate-sitemap": "node scripts/generate-sitemap.js"
}
```

---

## 3-5. JSON-LD 仕様（Schema.org）

### 目的
ページ内容を構造化データで明示し、AI検索の理解精度を向上。

### 主要スキーマタイプ
1. **Organization** - 企業・団体情報
2. **Article** - 記事・ブログ投稿
3. **FAQPage** - FAQ専用ページ
4. **Product** - 商品情報
5. **BreadcrumbList** - パンくずリスト

---

### 配置方法
```html
<head>
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "タイプ名",
    "プロパティ名": "値"
  }
  </script>
</head>
```

---

## 3-6. JSON-LD 実装：Organization

### 全技術共通テンプレート
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "株式会社サンプル",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "description": "○○業界のソリューションプロバイダー",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "1-2-3 サンプル町",
    "addressLocality": "東京都",
    "postalCode": "100-0001",
    "addressCountry": "JP"
  },
```

---

```json
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+81-3-1234-5678",
    "contactType": "customer service",
    "email": "info@example.com"
  },
  "sameAs": [
    "https://twitter.com/example",
    "https://www.facebook.com/example",
    "https://www.linkedin.com/company/example"
  ]
}
```

**配置ページ：** トップページ・会社概要ページ

---

## 3-7. JSON-LD 実装：Article
### ブログ記事・ニュース用
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "記事タイトル（60文字以内）",
  "image": "https://example.com/article-image.jpg",
  "author": {
    "@type": "Person",
    "name": "著者名"
},
  "publisher": {
    "@type": "Organization",
    "name": "株式会社サンプル",
    "logo": {
      "@type": "ImageObject",
      "url": "https://example.com/logo.png"
    }
},
  "datePublished": "2025-10-15",
  "dateModified": "2025-10-15",
  "description": "記事の要約（160文字以内）"
}

```

---

### WordPress実装例
```php
// single.php のhead内に追記
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "<?php the_title(); ?>",
  "image": "<?php echo get_the_post_thumbnail_url(); ?>",
  "author": {
    "@type": "Person",
    "name": "<?php the_author(); ?>"
  },
  "datePublished": "<?php echo get_the_date('c'); ?>",
  "dateModified": "<?php echo get_the_modified_date('c'); ?>"
}
</script>

```

---

## 3-8. JSON-LD 実装：FAQ
### FAQ専用ページ用
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "質問1のテキスト",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "回答1のテキスト"
      }
    }
  ]
}

```

---

### React実装例（react-helmet使用）
```jsx
import { Helmet } from 'react-helmet';

const FAQPage = ({ faqs }) => {
  const schemaData = {
    "@context": "https://schema.org",
    "@type": "FAQPage",
    "mainEntity": faqs.map(faq => ({
      "@type": "Question",
      "name": faq.question,
      "acceptedAnswer": {
        "@type": "Answer",
        "text": faq.answer
      }
    }))
  };

  return (
    <>
      <Helmet>
        <script type="application/ld+json">
          {JSON.stringify(schemaData)}
        </script>
      </Helmet>
      {/* FAQ表示部分 */}
    </>
  );
};
```

---

## 3-9. 検証方法

### 手順1：Google Rich Results Test
1. [https://search.google.com/test/rich-results](https://search.google.com/test/rich-results) にアクセス
2. URLまたはコードを入力
3. エラー・警告がないか確認

### 手順2：構文チェック
```bash
# JSON-LDの構文チェック（jqコマンド使用）
curl https://example.com/ | grep -oP '(?<=<script type="application/ld\+json">).*?(?=</script>)' | jq .
```

### 手順3：Schema.org Validator
- [https://validator.schema.org/](https://validator.schema.org/)
- JSON-LDコードを貼り付けて検証

---

## 3-10. Layer 2 完了チェックリスト

### Sitemap確認
- [ ] sitemap.xml ファイル配置完了（ルート直下）
- [ ] 全10ページのURLを記載
- [ ] lastmod（最終更新日）を各ページに設定
- [ ] priority設定（トップ1.0、主要0.8、一般0.5）
- [ ] robots.txt にSitemap URLを記載済み
### JSON-LD確認
- [ ] Organization スキーマ実装（トップページ）
- [ ] Article スキーマ実装（ブログ記事ページ）
- [ ] FAQPage スキーマ実装（FAQページ）
- [ ] Google Rich Results Test で検証合格
- [ ] 構文エラーなし（jq / Schema.org Validator確認）

**完了条件：** すべて☑️でLayer 3へ進む

---

<!-- _class: chapter -->

# 第4章
## Layer 3: Content Optimization
### FAQ / 構造改善

---

## 4-1. コンテンツ最適化方針

### 目的
AI検索が**引用しやすい**コンテンツ構造に改善。

### 最適化対象
1. **FAQ追加** - 3-5個/ページ、明確なQ&A形式
2. **見出し構造** - H1→H2→H3の論理的階層
3. **メタディスクリプション** - 120-160文字、キーワード含む
4. **箇条書き強化** - 手順・特徴を箇条書き化

### 優先順位
- 高：トップページ、主要サービスページ
- 中：ブログ記事、事例紹介
- 低：利用規約、プライバシーポリシー

---

## 4-2. FAQ作成ガイドライン

### 良いFAQの条件
1. **1問1答** - 1つの質問に1つの明確な回答
2. **具体性** - 「よくある」ではなく実際の疑問点
3. **簡潔性** - 回答は3-5文、200文字以内
4. **検索意図** - ユーザーが実際に検索しそうな表現
### FAQ例（良い）
**Q：** 導入にかかる期間はどのくらいですか？  
**A：** 通常2-4週間です。ヒアリング（1週間）→設計（1週間）→実装・テスト（2週間）の流れで進めます。お急ぎの場合は最短10営業日での対応も可能です。
### FAQ例（悪い）
**Q：** サービスについて教えてください。  
**A：** 弊社のサービスは様々な業界でご利用いただいており、多くのお客様にご満足いただいております。詳細はお問い合わせください。

---

## 4-3. FAQ実装：WordPress版

### 方法1：Gutenbergブロック
```
1. 投稿編集画面で「+」ボタン
2. 「FAQ」ブロックを検索（プラグイン：Yoast SEO）
3. 質問・回答を入力
4. 公開
```

---

### 方法2：HTMLブロック
```html
<div class="faq-section">
  <div class="faq-item">
    <h3 class="faq-question">質問1のテキスト</h3>
    <div class="faq-answer">
      <p>回答1のテキスト</p>
    </div>
  </div>
  
  <div class="faq-item">
    <h3 class="faq-question">質問2のテキスト</h3>
    <div class="faq-answer">
      <p>回答2のテキスト</p>
    </div>
  </div>
</div>
```

**CSS追加（style.css）：**
```css
.faq-item { margin-bottom: 2rem; border-bottom: 1px solid #eee; }
.faq-question { font-size: 1.2rem; font-weight: bold; color: #333; }
.faq-answer { margin-top: 0.5rem; line-height: 1.6; }
```

---

## 4-4. FAQ実装：静的HTML版
### HTMLテンプレート
```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>よくある質問 | サンプル</title>
  <meta name="description" content="サービスに関するよくある質問と回答をまとめました。">
  <!-- JSON-LD (FAQPage) -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "FAQPage",
    "mainEntity": [
      {"@type": "Question",
      "name": "導入にかかる期間はどのくらいですか？",
      "acceptedAnswer": {
      "@type": "Answer",
      "text": "通常2-4週間です。ヒアリング（1週間）→設計（1週間）→実装・テスト（2週間）の流れで進めます。"}
    }
  ]
}
</script>
</head>

```

---

```html
<body>
  <main>
    <h1>よくある質問</h1>
    
    <section class="faq-item">
      <h2>導入にかかる期間はどのくらいですか？</h2>
      <p>通常2-4週間です。ヒアリング（1週間）→設計（1週間）→実装・テスト（2週間）の流れで進めます。お急ぎの場合は最短10営業日での対応も可能です。</p>
    </section>
    
    <section class="faq-item">
      <h2>料金体系を教えてください。</h2>
      <p>初期費用10万円〜、月額費用3万円〜です。ご利用規模に応じたプランをご用意しています。詳しくは<a href="/pricing/">料金ページ</a>をご覧ください。</p>
    </section>
  </main>
</body>
</html>

```

---

## 4-5. FAQ実装：React版
### コンポーネント化
```jsx
// components/FAQ.jsx
import React, { useState } from 'react';
import { Helmet } from 'react-helmet';

const FAQ = ({ items }) => {
  const [openIndex, setOpenIndex] = useState(null);
  const schemaData = {
    "@context": "https://schema.org",
    "@type": "FAQPage",
    "mainEntity": items.map(item => ({
      "@type": "Question",
      "name": item.question,
      "acceptedAnswer": {
        "@type": "Answer",
        "text": item.answer
      }
    }))
  };

```
---

```jsx
  return (
    <>
      <Helmet>
        <script type="application/ld+json">
          {JSON.stringify(schemaData)}
        </script>
      </Helmet>
      
      <div className="faq-container">
        {items.map((item, index) => (
          <div key={index} className="faq-item">
            <h3 
              className="faq-question"
              onClick={() => setOpenIndex(openIndex === index ? null : index)}
            >
              {item.question}
            </h3>
            {openIndex === index && (
              <div className="faq-answer">
                <p>{item.answer}</p>
              </div>
            )}
          </div>
        ))}
      </div>
    </>
  );
};

export default FAQ;

```

---

### 使用例
```jsx
// pages/faq.jsx
const faqData = [
  {
    question: "導入にかかる期間はどのくらいですか？",
    answer: "通常2-4週間です。ヒアリング（1週間）→設計（1週間）→実装・テスト（2週間）の流れで進めます。"
  },
  // ... 他のFAQ
];

<FAQ items={faqData} />
```

---

## 4-6. 見出し構造改善（Before/After）

### Before（悪い例）
```html
<h2>サービス紹介</h2>
<p>弊社のサービスは...</p>

<h2>機能1</h2>
<p>機能1の説明...</p>

<h2>機能2</h2>
<p>機能2の説明...</p>

<h2>料金</h2>
<p>料金は...</p>
```

**問題点：** すべて同階層（H2）で、論理構造が不明確

---

### After（良い例）
```html
<h1>サービス名 - 業界特化型ソリューション</h1>
<h2>主な機能</h2>
<p>3つの主要機能で業務効率を改善します。</p>
<h3>機能1：自動化処理</h3>
<p>繰り返し作業を自動化し、工数を50%削減します。</p>
<ul>
  <li>データ取り込み自動化</li>
  <li>レポート生成自動化</li>
</ul>
<h3>機能2：リアルタイム分析</h3>
<p>データを即座に可視化し、意思決定を加速します。</p>
<h2>料金プラン</h2>
<p>3つのプランからお選びいただけます。</p>
<h3>スタータープラン</h3>
<p>月額3万円〜、小規模チーム向け。</p>
<h3>ビジネスプラン</h3>
<p>月額10万円〜、中規模企業向け。</p>
```

**改善点：** H1→H2→H3の階層構造、箇条書き活用

---

## 4-7. メタディスクリプション最適化

### ルール
1. **文字数：** 120-160文字（スマホ表示考慮）
2. **キーワード：** 主要キーワードを自然に含める
3. **CTA：** 行動喚起を含める（「詳しくはこちら」等）
4. **重複回避：** 各ページ固有の内容

### Before（悪い例）
```html
<meta name="description" content="株式会社サンプルの公式サイトです。">
```

### After（良い例）
```html
<meta name="description" content="業界特化型ソリューションで業務効率50%改善。自動化処理・リアルタイム分析で意思決定を加速。導入実績500社超、無料トライアル実施中。">
```

---

### WordPress実装
```php
// functions.php に追記
function custom_meta_description() {
    if (is_single()) {
        global $post;
        $description = mb_substr(strip_tags($post->post_content), 0, 120) . '...';
        echo '<meta name="description" content="' . esc_attr($description) . '">';
    }
}
add_action('wp_head', 'custom_meta_description');
```
---

### 静的HTML実装
```html
<head>
  <meta name="description" content="（各ページ固有の120-160文字）">
</head>
```
### React実装（react-helmet）
```jsx
<Helmet>
  <meta name="description" content="（各ページ固有の120-160文字）" />
</Helmet>
```

---

## 4-8. Layer 3 完了チェックリスト
### FAQ実装確認
- [ ] 各主要ページにFAQ 3-5個追加
- [ ] FAQ JSON-LDスキーマ実装
- [ ] 質問は検索意図を反映（具体的な表現）
- [ ] 回答は簡潔（3-5文、200文字以内）
### 見出し構造確認
- [ ] 全ページH1タグは1つのみ
- [ ] H2→H3の階層構造（H1→H3の飛ばしなし）
- [ ] 見出しに主要キーワード含む
- [ ] 箇条書きで要点整理（3-5項目/セクション）

---

### メタディスクリプション確認
- [ ] 全10ページに固有のdescription設定
- [ ] 文字数120-160文字
- [ ] 主要キーワード含む
- [ ] 重複なし（各ページユニーク）
**完了条件：** すべて☑️でLayer 4へ進む

---

<!-- _class: chapter -->

# 第5章
## Layer 4: Monitoring
### テスト / KPI測定

---

## 5-1. KPI定義・測定方法

### 主要KPI（3項目）
1. **言及率** - AI検索での企業名・サービス名の言及頻度
2. **引用精度** - 情報の正確性（誤情報の有無）
3. **競合比較順位** - 競合との比較時の順位・ポジション

### 測定頻度
- **週次：** ChatGPT/Perplexityテスト（30分/週）
- **月次：** 競合比較・KPI集計（2時間/月）
- **四半期：** 改善施策レビュー・優先順位再設定

---

## 5-2. ChatGPTテスト手順

### 準備
- ChatGPT（無料版でOK）にログイン
- テストプロンプト集を用意（5-10パターン）

---

### テスト実行
```
【プロンプト例1】
「[業界]の課題を解決する方法を教えてください」

【プロンプト例2】
「[競合A]と[自社サービス]を比較してください」

【プロンプト例3】
「[自社サービス名]について詳しく教えてください」

【プロンプト例4】
「[業界]で最も評価の高いソリューションは何ですか？」

【プロンプト例5】
「[特定の課題]を解決するツールを3つ挙げてください」
```
---

### チェック項目
- ✅ 企業名・サービス名が言及されているか
- ✅ 引用元にサイトURLが含まれるか
- ✅ 情報の正確性（誤情報・古い情報がないか）
- ✅ 競合との比較時のポジション（1-3位目標）

---

## 5-3. Perplexityテスト手順

### 準備
- Perplexity（https://www.perplexity.ai/）にアクセス
- 検索キーワードリストを用意

---

### テスト実行
```
【検索ワード例1】
「[業界名] ソリューション 比較」

【検索ワード例2】
「[課題キーワード] 解決方法」

【検索ワード例3】
「[製品カテゴリ] おすすめ」

【検索ワード例4】
「[自社サービス名] 評判」

【検索ワード例5】
「[競合サービス] vs [自社サービス]」
```
---

### チェック項目
- ✅ 上位3件の引用ソースに含まれるか
- ✅ 引用されるコンテンツの種類（トップ/FAQ/ブログ等）
- ✅ 競合との並び順（何番目に表示されるか）
- ✅ 要約文の内容（意図通りの情報が伝わっているか）

---

## 5-4. 週次チェックフロー
### タイミング
- 毎週金曜日午後（30分確保）

### 手順
```
1. ChatGPTテスト（15分）
   - プロンプト5個を実行
   - 言及有無・引用URL・情報精度をスプレッドシートに記録

2. Perplexityテスト（10分）
   - 検索ワード5個を実行
   - 引用順位・並び順を記録

3. 前週比較（5分）
   - 改善/悪化箇所を特定
   - 要因を簡易分析（コンテンツ更新・競合動向）

4. アクション決定（5分）
   - 改善が必要なページ・項目を1つ選定
   - 次週の修正タスク化

```

---

## 5-5. 改善優先度判定

### マトリクス（効果×工数）

| 優先度 | 効果 | 工数 | 例 |
|-------|------|------|-----|
| **P0（即対応）** | 高 | 低 | メタディスクリプション修正 |
| **P1（Week内）** | 高 | 中 | FAQ追加・JSON-LD修正 |
| **P2（Month内）** | 中 | 中 | 見出し構造全体見直し |
| **P3（検討）** | 低 | 高 | サイト全体リニューアル |

---

### 判定フロー
```
1. 効果判定
   - 言及率が低い → 効果【高】
   - 引用精度が低い → 効果【中】
   - 競合順位が低い → 効果【高】

2. 工数判定
   - テキスト修正のみ → 工数【低】
   - HTML/CSS修正 → 工数【中】
   - システム改修 → 工数【高】

3. 優先度決定
   - 効果×工数マトリクスで判定
   - P0 → P1 → P2 の順に対応
```

---

## 5-6. 測定データ記録フォーマット

### スプレッドシート例

| 日付 | ツール | プロンプト/検索ワード | 言及有無 | 引用URL | 順位 | メモ |
|------|--------|---------------------|---------|---------|------|------|
| 2025-10-15 | ChatGPT | [業界]の課題解決方法 | ○ | example.com/faq | - | FAQ引用あり |
| 2025-10-15 | ChatGPT | [自社]について | ○ | example.com/ | - | 正確な情報 |
| 2025-10-15 | Perplexity | [製品] 比較 | ○ | example.com/services | 2位 | 競合Aの次 |
| 2025-10-15 | Perplexity | [課題] 解決 | × | - | - | 言及なし |

---

### 月次集計例
```
【2025年10月サマリー】
- 言及率：60%（12/20テスト）
- 引用URL：トップページ40%、FAQ30%、ブログ20%
- 平均順位：2.3位（競合3社比較）
- 改善箇所：ブログ記事のJSON-LD追加で引用率+10%

【Next Action】
- P0：トップページのメタディスクリプション修正（金曜完了）
- P1：製品ページにFAQ追加（来週水曜完了）
```

---

## 5-7. Layer 4 完了チェックリスト
### 測定環境準備
- [ ] ChatGPTアカウント準備
- [ ] Perplexityアクセス確認
- [ ] テストプロンプト集作成
- [ ] 検索キーワードリスト作成
- [ ] 記録用スプレッドシート作成
### 初回測定実施
- [ ] ChatGPTテスト実施（5～プロンプト×結果記録）
- [ ] Perplexityテスト実施（5検索ワード×結果記録）
- [ ] ベースライン（現状値）確定
- [ ] 改善目標設定（1ヶ月後の目標値）

**完了条件：** すべて☑️で実装フェーズ完了

---

<!-- _class: chapter -->

# 第6章
## 実装フロー

---

## 6-1. 実装順序・担当分担

### フェーズ1：基礎実装（Week 1）

| 作業 | 担当 | 工数 | 完了条件 |
|------|------|------|---------|
| robots.txt作成 | インフラ | 0.5日 | ブラウザアクセス確認 |
| llms.txt作成 | PM/マーケ | 1日 | 内容レビュー承認 |
| Sitemap生成 | バックエンド | 1日 | 全URL含む・検証OK |
| JSON-LD (Organization) | フロントエンド | 0.5日 | Rich Results Test合格 |

---

### フェーズ2：コンテンツ最適化（Week 2）

| 作業 | 担当 | 工数 | 完了条件 |
|------|------|------|---------|
| FAQ作成（5ページ） | マーケ/PM | 2日 | 3-5個/ページ |
| JSON-LD (FAQ) | フロントエンド | 1日 | Rich Results Test合格 |
| 見出し構造改善 | フロントエンド | 1日 | 全ページH1-H3階層化 |
| メタディスクリプション | マーケ | 1日 | 120-160文字・重複なし |

---

### フェーズ3：測定・改善（Week 3）

| 作業 | 担当 | 工数 | 完了条件 |
|------|------|------|---------|
| 測定環境準備 | PM | 0.5日 | スプレッドシート完成 |
| 初回測定 | マーケ | 0.5日 | ベースライン確定 |
| 改善優先度判定 | PM/マーケ | 0.5日 | P0-P3分類完了 |

---

## 6-2. ページ別実装チェックシート

### 使い方
各ページごとに本シートをコピーし、実装状況を管理。

---

### ページ名：[ トップページ ]

#### Layer 1: Crawler Control
- [ ] robots.txt で許可確認
- [ ] llms.txt にURL記載

#### Layer 2: Discoverability
- [ ] Sitemap にURL記載（priority: 1.0）
- [ ] JSON-LD (Organization) 実装
- [ ] パンくずリスト実装（該当する場合）

---

#### Layer 3: Content Optimization
- [ ] FAQ追加（3-5個）
- [ ] 見出し構造確認（H1=1個、H2-H3階層）
- [ ] メタディスクリプション設定（120-160文字）
- [ ] 箇条書き活用（3箇所以上）

#### Layer 4: Monitoring
- [ ] ChatGPTテスト実施
- [ ] Perplexityテスト実施
- [ ] 言及率・引用URL記録

**完了日：** [ 2025-10-__ ]  
**レビュー担当：** [ 名前 ]

---

### ページ名：[ サービス紹介 ]

（同様のチェック項目を繰り返し...）

---

## 6-3. リリース前最終確認

### チェックリスト（全体）

#### ファイル配置
- [ ] robots.txt 配置確認（https://example.com/robots.txt）
- [ ] llms.txt 配置確認（https://example.com/llms.txt）
- [ ] sitemap.xml 配置確認（https://example.com/sitemap.xml）

#### 全ページ共通
- [ ] 10ページすべてSitemapに記載
- [ ] 各ページのメタディスクリプション重複なし
- [ ] 各ページのH1タグは1つのみ
- [ ] JSON-LDエラーなし（Rich Results Test全合格）

---

#### 技術検証
- [ ] 全ページ表示確認（404なし）
- [ ] スマホ表示確認（レスポンシブ対応）
- [ ] ページ速度確認（PageSpeed Insights 70点以上）
- [ ] curl -A "GPTBot" でアクセス成功

#### 測定準備
- [ ] テストプロンプト5個準備
- [ ] 検索キーワード5個準備
- [ ] スプレッドシート共有設定
- [ ] 週次チェック担当者・日時確定

**最終レビュー担当：** [ PM名 ]  
**リリース予定日：** [ 2025-10-__ ]

---

## 6-4. 運用移行・引き継ぎ

### 運用タスク一覧

| タスク | 頻度 | 担当 | 所要時間 | ツール |
|--------|------|------|---------|--------|
| 週次テスト | 毎週金曜 | マーケ | 30分 | ChatGPT/Perplexity |
| 月次レビュー | 毎月末 | PM/マーケ | 1時間 | スプレッドシート |
| コンテンツ更新 | 随時 | マーケ | - | CMS |
| 競合調査 | 四半期 | PM | 2時間 | 各種ツール |

---

### 引き継ぎドキュメント
1. **本仕様書** - 技術実装の全体像
2. **プロンプト集** - ChatGPT/Perplexityテスト用
3. **スプレッドシート** - 測定データ記録用
4. **改善事例集** - 過去の改善施策と効果

### サポート体制
- **技術質問：** [ 開発リーダー名 ] - Slack: #web-projects
- **コンテンツ質問：** [ マーケ責任者名 ] - Slack: #marketing
- **緊急対応：** [ PM名 ] - Email: pm@example.com

---

## 6-5. トラブルシューティング（再掲）

### よくあるエラーと対処法

| 症状 | 原因 | 解決策 |
|------|------|--------|
| **robots.txt 404** | ファイル配置ミス | ルート直下に配置確認 |
| **JSON-LDエラー** | 構文ミス | Rich Results Testで検証 |
| **Sitemap読込失敗** | XML形式エラー | バリデーターで検証 |
| **言及率0%** | クローラーブロック | robots.txtでAllow確認 |
| **引用精度低い** | コンテンツ不明確 | FAQ・見出し再構成 |

### エスカレーション基準
- **Level 1（自己解決）：** 上記表の対処法で解決
- **Level 2（チーム相談）：** 1時間試して解決しない場合
- **Level 3（外部支援）：** 技術的に対応不可と判断した場合

---

## 付録A：用語集

| 用語 | 説明 |
|------|------|
| **LLMO** | LLM Optimization - AI検索エンジン最適化 |
| **RAG** | Retrieval-Augmented Generation - 検索拡張生成 |
| **JSON-LD** | JavaScript Object Notation for Linked Data - 構造化データ形式 |
| **Schema.org** | 構造化データの標準仕様 |
| **robots.txt** | クローラー制御ファイル |
| **llms.txt** | AI検索エンジン向けサイト情報ファイル |
| **Sitemap** | サイト構造を示すXMLファイル |
| **User-agent** | クローラーの識別名 |
| **Rich Results** | Google検索の構造化データ表示 |
| **KPI** | Key Performance Indicator - 重要業績評価指標 |

---

## 付録B：参考リンク集

### 公式ドキュメント
- Google Search Central: https://developers.google.com/search
- Schema.org: https://schema.org/
- robots.txt仕様: https://www.robotstxt.org/

### 検証ツール
- Google Rich Results Test: https://search.google.com/test/rich-results
- Schema.org Validator: https://validator.schema.org/
- PageSpeed Insights: https://pagespeed.web.dev/

### AI検索エンジン
- ChatGPT: https://chat.openai.com/
- Perplexity: https://www.perplexity.ai/
- Google Gemini: https://gemini.google.com/

---

## 付録C：次ステップ

### フェーズ2（3ヶ月後〜）
1. **高度なJSON-LD実装**
   - Product（商品情報）
   - Review（レビュー）
   - HowTo（手順）

2. **コンテンツ拡充**
   - 事例紹介ページ作成
   - ホワイトペーパー公開

---

3. **競合分析強化**
   - 競合5社の月次追跡
   - ベンチマーク指標設定
   - 差別化ポイント明確化

### フェーズ3（6ヶ月後〜）
- OpenAPI仕様書公開（開発者向け）
- ナレッジベース構築（RAG最適化）
- 多言語対応（英語版サイト）