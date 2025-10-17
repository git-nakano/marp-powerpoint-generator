---

marp: true
theme: default
paginate: true
class: lead
title: 「SEO記事 × AIO/LLMO」実行チェックリスト（エンジニア向け解説）
description: ReSkill Hub / 経営者向けAI戦略研修のLP観点とSEO記事リライト標準の内容
-------------------------------------------------------------------------------------

# SEO記事 × AIO/LLMO

## 実行チェックリスト（エンジニア向け）

* 対象：LP/記事の実装・改修を行うエンジニア、テックリード
* 目的：検索流入（SEO）を維持しつつ、AI回答面（AI Overview/LLM引用）で“誤解なく・引用されやすい”状態を作る
* 出典：LP監査の要点と記事リライト標準手順を統合し、技術的観点を補強

  * 参考LP観察に基づくAIO/LLMOチェック（要点抜粋） 
  * SEO記事→AIO対応リライト手順（要点抜粋） 

---

## まずは優先Top10（影響大 × 実装コスト低）

1. FAQの**FAQPage**構造化データ化（JSON-LD）
2. **年入り**開催日程＋`Event`構造化データ（各回ISO 8601）
3. 住所・TEL等を**Organization/LocalBusiness**に統合
4. 冒頭に**要約ボックス**（Who/What/Outcome/When/How）
5. **スケジュール表**をHTMLテキストで（画像NG）
6. **CTAラベル統一**＋`aria-label`明示
7. **対象者/前提/成果物**を箇条書きで定型化
8. **E-E-A-T強化**（講師・運営・sameAs）
9. **誤解Q&A**を3件以上追加（反論処理）
10. **OG/Twitterカード**とメタ整合
    （1–10はLP監査結果を抽出し技術化 ）

---

## 記事リライト × AIOの基本原則

* 冒頭**結論・要約** → AIが拾いやすい先頭配置
* **Q&A/FAQブロック**・**質問系見出し**・**箇条書き/表**を多用
* **出典リンク**・**著者/監修**・**最終更新日**を明示
* **Schema.org**（Article/FAQPage/HowTo/BreadcrumbList）
* **セマンティックHTML**（`<main> <article> <section>`）
* **AIクローラー許可**（robots.txt / meta robots）
* **ゼロクリック対応**：「短い答え」＋「詳細解説」二段構成
  （実務向けチェック要点を統合整理 ）

---

## スプリント計画（推奨）

* Day 1–2：要約ボックス・表・FAQ・CTA整備（Top10の1,4–7,9）
* Day 3：JSON-LD（Organization/FAQPage/Event/Article）実装
* Day 4：OG/メタ/robots/サイトマップ/CLS・LCP対策
* Day 5：KPI・監視設定、ABテスト用の計測埋め込み

---

## チェックリスト A：コンテンツ設計

* [ ] 冒頭「要約ボックス」：対象/目的/形式/期間/成果/申込
* [ ] **年入り日付**と**開催表**（回/テーマ/日付/時間/場所/締切）
* [ ] 見出しを**質問文**に（例：AIOとは？ 実装は？）
* [ ] **FAQ（既存＋誤解Q&A）**を最下部に集約
* [ ] **対象/前提/成果**の定型ブロック（Who/Prereq/Outcome）
* [ ] 画像は**意味あるalt**（図の要点を10–20字）
  （LPの現状差分に対応する実務タスク ）

---

## チェックリスト B：構造化データ（JSON-LD）

* [ ] `Organization`/`LocalBusiness`：`name/url/telephone/address/sameAs`、`contactPoint`
* [ ] `Article`：記事/LP本文に対応、`headline/dateModified/author`
* [ ] `FAQPage`：FAQをそのままJSON-LD化
* [ ] `Event`：**各回**に`startDate/endDate`（ISO 8601, +09:00）、`location/organizer/offers`
* [ ] `BreadcrumbList`：サイト脈絡を明示
* [ ] `Speakable`（任意）：要約ボックスの2–3文
  （Event/FAQ/Org設計はLP要件準拠  ／ Article/FAQ運用は手順書準拠 ）

---

## チェックリスト C：技術（クロール & 表示）

* [ ] `<html lang="ja">` / `hreflang`（必要時）
* [ ] `canonical`の一意化（UTM付の正規化）
* [ ] **robots.txt**：OAI-SearchBot/AIスクレイパーを**ブロックしない**方針を明示
* [ ] **XMLサイトマップ**にLP/記事を登録
* [ ] テーブルは**テキスト**、画像にしない
* [ ] **CLS/LCP**：ヒーロー画像の`width/height`、`loading="lazy"`、フォントpreload
  （手順書「AIクローラー許可」「セマンティックHTML」を技術に落とし込み ）

---

## チェックリスト D：信頼性（E-E-A-T）

* [ ] **著者/監修**：肩書・略歴・実績（検証可能な数字）
* [ ] **第三者の声/掲載**：ロゴ・リンク・出典
* [ ] **ポリシー導線**：特商法/プライバシー/利用規約
* [ ] **sameAs**：公式X/会社サイト/外部プロフィール
  （LPの信頼シグナル強化を仕様化 ）

---

## チェックリスト E：計測・運用

* [ ] **AI引用KPI**：Google AI Overview / Perplexity / ChatGPTで**出典化率**を定点観測
* [ ] **SEO順位KPI**：従来KPIと**併走**
* [ ] **FAQログ**：問い合わせ・営業QAから継続拡充
* [ ] **更新ログ**：料金/日程変更時は**更新日**を本文・`dateModified`に反映
* [ ] **リライトサイクル**：3–6ヶ月ごとに棚卸し
  （KPI併走・定点観測はリライト運用の中核 ）

---

## 実装スニペット：Organization + ContactPoint

```html
<script type="application/ld+json">
{
 "@context": "https://schema.org",
 "@type": "Organization",
 "name": "（貴社名）",
 "url": "https://example.com/",
 "telephone": "+81-XX-XXXX-XXXX",
 "address": {
   "@type": "PostalAddress",
   "addressCountry": "JP",
   "addressRegion": "都道府県",
   "addressLocality": "市区町村",
   "streetAddress": "丁目番地"
 },
 "contactPoint": [{
   "@type": "ContactPoint",
   "contactType": "customer support",
   "telephone": "+81-XX-XXXX-XXXX",
   "areaServed": "JP",
   "availableLanguage": ["ja"]
 }],
 "sameAs": [
   "https://example.com/about",
   "https://x.com/your_official"
 ]
}
</script>
```

（Org/連絡先はLP現状の検証可能データを反映 ）

---

## 実装スニペット：Event（各回を個別に）

```html
<script type="application/ld+json">
{
 "@context": "https://schema.org",
 "@type": "Event",
 "name": "第1回：AIの基本理解と経営活用の可能性",
 "description": "AIとは何か／最新動向／経営インパクト。ゴール：基礎理解と自社活用の可能性把握。",
 "startDate": "2025-04-14T18:00:00+09:00",
 "endDate": "2025-04-14T20:00:00+09:00",
 "eventAttendanceMode": "https://schema.org/OfflineEventAttendanceMode",
 "location": {
   "@type": "Place",
   "name": "（会場名）",
   "address": { "@type": "PostalAddress", "addressCountry": "JP", "addressRegion": "大阪府" }
 },
 "organizer": { "@type": "Organization", "name": "（貴社名）", "url": "https://example.com/" },
 "offers": { "@type": "Offer", "price": "0", "priceCurrency": "JPY", "availability": "https://schema.org/InStock" }
}
</script>
```

（**年入り日付**・各回Eventの付与は最優先タスク ）

---

## 実装スニペット：FAQPage（雛形）

```html
<script type="application/ld+json">
{
 "@context": "https://schema.org",
 "@type": "FAQPage",
 "mainEntity": [
  {
   "@type": "Question",
   "name": "初心者でも参加できますか？",
   "acceptedAnswer": { "@type": "Answer", "text": "はい。基礎から解説します。" }
  },
  {
   "@type": "Question",
   "name": "全日程の参加は必須ですか？",
   "acceptedAnswer": { "@type": "Answer", "text": "各回完結型ですが通期参加を推奨します。" }
  },
  {
   "@type": "Question",
   "name": "助成金の対象になりますか？",
   "acceptedAnswer": { "@type": "Answer", "text": "条件により対象となる場合があります。詳細はお問い合わせください。" }
  }
 ]
}
</script>
```

（既存FAQ＋「よくある誤解」Q&Aの拡充を反映  ）

---

## 実装スニペット：Article（記事側のAIO化）

```html
<script type="application/ld+json">
{
 "@context": "https://schema.org",
 "@type": "Article",
 "headline": "経営者向けAI戦略：AIO/LLMO最適化の実務ガイド",
 "datePublished": "2025-10-01",
 "dateModified": "2025-10-17",
 "author": { "@type": "Person", "name": "（著者名）" },
 "publisher": { "@type": "Organization", "name": "（貴社名）" },
 "mainEntityOfPage": { "@type": "WebPage", "@id": "https://example.com/ai-strategy-aio" }
}
</script>
```

（**最終更新日**の明示・Articleスキーマ適用はAIO面でも重要 ）

---

## robots.txt / メタの推奨

```
# 主要AIクローラーは許可する（方針に応じて調整）
User-agent: *
Disallow:

Sitemap: https://example.com/sitemap.xml
```

```html
<!-- 記事/LPのメタ例 -->
<link rel="canonical" href="https://example.com/lp4/">
<meta name="robots" content="index,follow">
<meta property="og:type" content="website">
<meta property="og:title" content="経営者向けAI戦略研修 | 要点サマリー">
<meta property="og:description" content="誰向け/何が学べる/成果/申込方法を3行で要約。">
<meta property="og:image" content="https://example.com/ogp/ai-training.jpg">
```

（AIクローラー許可・OG整合は実装必須項目 ）

---

## スケジュール表（HTMLテキスト例）

```html
<table class="schedule">
  <thead>
    <tr><th>回</th><th>テーマ</th><th>日付</th><th>時間</th><th>形式/会場</th><th>締切</th></tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td><td>AIの基本理解と経営活用</td>
      <td>2025年4月14日(月)</td><td>18:00–20:00</td>
      <td>会場（大阪）/ オンライン有</td><td>2025年4月7日(月)</td>
    </tr>
    <!-- 回2〜7... -->
  </tbody>
</table>
```

（**画像ではなくテキスト**で提供すること ）

---

## 要約ボックス（UIコンポーネント例）

```html
<section class="summary" aria-labelledby="summary-title">
  <h2 id="summary-title">要約</h2>
  <ul>
    <li><strong>対象：</strong> 経営者/役員</li>
    <li><strong>目的：</strong> 自社AI戦略と実装計画の策定</li>
    <li><strong>形式：</strong> 全7回 / 各120分（大阪万博期間中）</li>
    <li><strong>成果：</strong> 施策ロードマップ、PoC計画、評価指標</li>
    <li><strong>申込：</strong> 下記CTAから（資料請求/相談/申込を分離）</li>
  </ul>
</section>
```

（LP要件を抽出し定型化。AI抽出の“冒頭要約”として機能させる ）

---

## CTA/アクセシビリティの実装

```html
<a class="btn btn-primary"
   href="/apply"
   aria-label="経営者向けAI戦略研修の申込み">申込み</a>

<a class="btn btn-outline"
   href="/contact"
   aria-label="経営者向けAI戦略研修に関する無料相談">無料相談</a>

<a class="btn btn-ghost"
   href="/assets/ai-training-guide.pdf"
   aria-label="研修資料のダウンロード">資料請求</a>
```

* ラベルは目的別に一意化、`aria-label`で意図を言語化（LLM抽出の補助にも有効） 

---

## 記事テンプレ：ゼロクリック構成

```markdown
# 結論（3行要約）
- なにが：……
- なぜ：……
- どうする：……

## 短い答え
……（100–150字）

## 詳しい解説
……

## よくある質問（FAQ）
- Q: 〜？
  - A: 〜。

## 参考・出典
- 公式/一次情報リンク…
```

（「短い答え＋詳細解説」＋FAQを記事内に同居させる作法 ）

---

## モニタリング設計（KPI例）

* **AI出典化率**：AI Overview/Perplexity/ChatGPTで週次サンプル
* **SEO順位**：対象クエリ群のGSC/順位計測
* **FAQ追加率**：インバウンド質問→FAQ反映のリードタイム
* **更新ログ整備率**：`dateModified`と本文の**更新日**の一致率
  （“AI引用”と“SEO”の二軸でKPI運用する方針 ）

---

## 品質ゲート（PR時の確認項目）

* [ ] 先頭要約が**3–5行**で完結
* [ ] **年入り日付**／ISO 8601の整合（本文・JSON-LD）
* [ ] FAQは**3件以上の誤解Q&A**を含む
* [ ] **構造化データの検証**（Rich Results Test）
* [ ] 画像は**意図的alt**、テーブルは**テキスト**
* [ ] **OG/メタ/カノニカル**の整合
* [ ] **robots.txt**でAIクローラー許可
* [ ] **LCP < 2.5s / CLS < 0.1**（Core Web Vitals）

---

## 付録：開発者Tips

* **生成AIでの抽出耐性**を上げる要点

  * 固有値（年・場所・金額・回次）を**テキスト**で近接配置
  * セクション見出しは**機能名/質問文**で規格化
  * CTAは**1意図=1ラベル**で一貫性
* **構造化データの更新**は**deployフック**で自動生成（YAML→JSON-LD）
* **翻訳/多言語**時は`hreflang`と`inLanguage`プロパティも同期