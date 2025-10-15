---
marp: true
theme: corporate-blue
paginate: true
---

<!-- _class: lead -->
# LLM思考プロセス詳細解説

### エンジニア向け技術解説
2025年10月

---

## 本プレゼンの目的

**対象**: 
- エンジニア
- プロンプトエンジニア
- AI活用担当者

**学べること**:
- AIがどのように複雑なタスクを処理するか
- 効果的なプロンプトの書き方
- 情報の信頼性を判断する方法

---

## このプレゼンで扱う実例

**作成した成果物**:
- LLMO技術最適化ガイド
- 8領域の技術仕様
- 実装チェックリスト
- コピペ可能なコード例

**所要時間**: 約15分

**使用機能**: Advanced Research（並列リサーチ）

---

## 思考プロセスの全体像

```
Phase 1: プロンプト解析 (5%)
  ↓
Phase 2: リサーチ戦略 (10%)
  ↓
Phase 3: 情報統合 (30%)
  ↓
Phase 4: コード生成 (25%)
  ↓
Phase 5-6: 品質保証 (15%)
  ↓
Phase 7-9: 最適化 (15%)
```

**総処理時間**: 約15分

---

<!-- _class: lead -->
# Phase 1
## プロンプト解析と要件抽出

**「指示を正しく理解する」フェーズ**

---

## Phase 1の目的

**解説**:
- 人間の指示（プロンプト）を機械が理解できる形に変換
- 「何を作るか」「どんな制約があるか」を整理
- 優先順位を決定

**例え**:
レストランで注文を受けるウェイターのように、
「何を」「いつまでに」「どのように」を整理する

---

## プロンプトの構造化

**入力プロンプトの構造**:
```
├── ペルソナ（どんな専門家として回答するか）
├── 成果物の形式（報告書、コード、文書など）
├── 必須ルール（絶対に守るべき制約）
├── カバー範囲（調査すべき領域）
├── 参照実装（具体的なコード例）
├── チェックリスト（確認項目）
└── 追加指示（その他の要求）
```

**用語解説**:
- **プロンプト**: AIへの指示文のこと
- **ペルソナ**: AIがどんな役割で答えるか（例: SEO専門家）
- **参照実装**: 実際に動くコードの見本

---

## 要件の優先順位付け（1/2）

```python
def prioritize_tasks(self):  # タスクの優先順位を決める関数
    return [  # リスト（配列）を返す
        # ('項目名', '優先度', '変化速度')の3つ組
        ('AI crawler UAs', 'CRITICAL', 'changes monthly'),
        ('Schema.org specs', 'HIGH', 'stable but version-dependent'),
        ('OpenAPI best practices', 'HIGH', 'rapidly evolving'),
        ('Legal compliance', 'MEDIUM', 'Japan-specific, stable'),
        ('Monitoring tools', 'MEDIUM', 'market fragmented')
    ]
```

**用語解説**:
- **AI crawler**: AIがウェブサイトを巡回するプログラム
- **UA (User Agent)**: ブラウザやクローラーの識別情報
- **Schema.org**: 構造化データの標準規格
- **OpenAPI**: API仕様書の業界標準フォーマット

---

## 要件の優先順位付け（2/2）

**解説**:

**変化が速い情報 = 優先度高**
- 例: スマホアプリのバージョン → すぐ古くなる
- 例: 法律 → めったに変わらない

**戦略**: 変化の速いものから調査開始

---

## 実行可能性の事前評価

| 項目 | 可能? | 対策 |
|-----|-------|------|
| 15分で8領域カバー | ✓ | 並列処理 |
| 日本法務情報 | ✓ | 公開情報多数 |
| AIクローラーIP範囲 | △ | UA文字列で代替 |
| コピペ可能コード | ✓ | 検証コマンド付与 |

**TIPS**: 
完璧を目指さず、実行可能な範囲で最善を尽くす

---

<!-- _class: lead -->
# Phase 2
## リサーチ戦略と実行計画

**「どこから情報を集めるか」を決めるフェーズ**

---

## Phase 2の目的

**解説**:
- 信頼できる情報源を特定
- 効率的な検索クエリを設計
- 情報の優先順位を決定

**例え**:
図書館で本を探すとき、
「どの棚から」「どんなキーワードで」探すか決める

---

## 3層リサーチアーキテクチャ（1/3）

**Layer 1: 公式情報（Primary Sources）**
- OpenAI Platform Docs（GPTBotの仕様書）
- Anthropic Help Center（ClaudeBotの説明）
- Schema.org（構造化データの標準規格）
- 日本政府機関（法律・ガイドライン）

**用語解説**:
- **Platform Docs**: 公式の技術ドキュメント
- **GPTBot/ClaudeBot**: 各社のAIクローラープログラム
- **構造化データ**: 機械が理解しやすい形式のデータ

**信頼性**: ⭐⭐⭐⭐⭐ (10/10)

---

## 3層リサーチアーキテクチャ（2/3）

**Layer 2: 業界情報**
- SEO専門メディア
- 技術ブログ（Cloudflare等）
- 監視ツールベンダー

**信頼性**: ⭐⭐⭐⭐ (8-9/10)

**TIPS**: 
複数のソースで確認することが重要

---

## 3層リサーチアーキテクチャ（3/3）

**Layer 3: 問題事例**
- Perplexityのrobots.txt無視事件
- Bytespiderの過負荷問題
- Google-Extendedの制限

**目的**: 
「落とし穴」を事前に知る

---

## 段階的クエリ拡張戦略

```python
class SearchQueryGenerator:  # 検索クエリを生成するクラス
    def generate_queries(self, topic):  # topicを受け取る関数
        queries = []  # 空のリストを作成（検索語を格納）
        
        # Stage 1: 広範囲の検索（全体像を把握）
        queries.append(f"LLMO {topic} 2025")  # f文字列で変数を埋め込み
        
        # Stage 2: 技術詳細の検索（具体的な実装方法）
        queries.append(f"{topic} implementation guide")
        
        # Stage 3: 公式ソースの検索（site:で特定ドメイン指定）
        queries.append(f"site:docs.anthropic.com {topic}")
        
        # Stage 4: 問題事例の検索（既知の課題を調査）
        queries.append(f"{topic} problems issues 2024 2025")
        
        return queries  # 生成した検索クエリのリストを返す
```

**コード解説**:
- `class`: オブジェクト指向プログラミングのクラス定義
- `def`: 関数（メソッド）の定義
- `f"..."`: f文字列（変数を埋め込める文字列）
- `append()`: リストに要素を追加するメソッド
- `site:`: Google検索で特定サイト内を検索する演算子

---

## 情報信頼性スコアリング

| ソース | 信頼性 | 使用条件 |
|--------|--------|---------|
| 公式ドキュメント | 10/10 | 最優先 |
| W3C/Schema.org | 10/10 | 仕様準拠 |
| 技術ブログ | 9/10 | 詳細参考 |
| Stack Overflow | 7/10 | 実装参考 |
| 個人ブログ | 5/10 | 要検証 |

**ルール**: 公式 > コミュニティ

---

## 相反情報の解決ロジック

```python
def resolve_conflicting_info(sources):  # sourcesは情報源のリスト
    # Rule 1: 公式情報を最優先（if文で条件判定）
    if has_official_source(sources):  # 公式情報が含まれているか？
        return filter_official(sources)  # 公式情報だけを返す
    
    # Rule 2: 最新情報を優先（ただし信頼性も考慮）
    if all_recent(sources):  # 全て最近の情報か？
        return most_credible(sources)  # 最も信頼できるものを返す
    
    # Rule 3: 複数ソースで一致する情報を優先
    consensus = find_consensus(sources)  # 共通見解を探す
    if consensus:  # 共通見解が見つかったら
        return consensus  # それを返す
    
    # Rule 4: 両方の意見を示し、推奨案を提示
    return present_alternatives_with_recommendation(sources)
```

**用語解説**:
- **conflicting info**: 矛盾する情報
- **sources**: 情報源（複数形）
- **official source**: 公式の情報源（企業や政府の公式サイト）
- **consensus**: コンセンサス（複数の情報源で一致する見解）
- **credible**: 信頼できる

**処理の流れ**: 公式→最新→多数決→両論併記の順で判断

---

<!-- _class: lead -->
# Phase 3
## 情報統合とナレッジグラフ構築

**「点の情報を線でつなぐ」フェーズ**

---

## Phase 3の目的

**解説**:
- バラバラの情報を整理
- 技術間の依存関係を理解
- 実装の順序を決定

**例え**:
パズルのピースを正しい位置に配置して、
全体像を完成させる作業

---

## メンタルモデル構築

```
LLMO Optimization Stack（最適化の4層構造）:

┌─────────────────────────────────┐
│ Layer 4: Monitoring & KPIs      │ ← 効果測定層
│         (監視・成果指標)         │
├─────────────────────────────────┤
│ Layer 3: Content Optimization   │ ← コンテンツ最適化層
│         (内容の改善)             │
├─────────────────────────────────┤
│ Layer 2: Discoverability        │ ← 発見可能性層
│         (見つけてもらう仕組み)  　│
├─────────────────────────────────┤
│ Layer 1: Crawler Control        │ ← クローラー制御層
│         (巡回プログラムの制御)  　│
└─────────────────────────────────┘
```

**用語解説**:
- **Stack**: 層（レイヤー）を重ねた構造
- **Monitoring**: 監視（状態を継続的に確認すること）
- **KPI**: Key Performance Indicator（重要業績評価指標）
- **Optimization**: 最適化（より良い状態にすること）
- **Discoverability**: 発見可能性（見つけやすさ）
- **Crawler**: クローラー（Webを自動巡回するプログラム）

**実装順序**: Layer 1（下）から順に実装

---

## 依存関係グラフ

```
robots.txt
  ↓ (制御)
Crawler Control
  ↓ (許可)
Sitemap Discovery
  ↓ (読取)
Content Crawling
  ↓ (解析)
Schema Parsing
  ↓ (学習)
LLM Knowledge Graph
  ↓ (表示)
AI Search Results
```

---

## Impact × Effort マトリクス

**実装の優先順位**:

| 効果 | 工数 | 項目 | 時期 |
|------|------|------|------|
| 高 | 低 | robots.txt | 今日 |
| 高 | 中 | Sitemap分割 | Week 1 |
| 中 | 高 | OpenAPI | Week 2-3 |
| 低 | 高 | RAG代替 | 3ヶ月 |

**TIPS**: 
「効果大・簡単」から着手

---

<!-- _class: lead -->
# Phase 4
## コンテンツ生成とコード品質保証

**「実際に作る」フェーズ**

---

## Phase 4の目的

**解説**:
- 実装可能なコードを生成
- 検証方法を明示
- エラー時の対処法を用意

**例え**:
料理のレシピに、
「味見の方法」と「失敗したときの対処法」も書く

---

## コード生成の品質基準

```python
class CodeGenerator:  # コード生成クラス
    def validate_code_sample(self, code):  # コードを検証する関数
        # checksは辞書型（キーと値のペア）
        checks = {
            # キー: チェック項目名, 値: チェック結果（True/False）
            'syntax_valid': self.check_syntax(code),
            # 構文が正しいか？（セミコロン忘れなど）
            
            'copy_paste_ready': self.has_complete_context(code),
            # コピペしてすぐ動くか？（import文など全て含む）
            
            'includes_comments': self.has_meaningful_comments(code),
            # 意味のあるコメントが書かれているか
            
            'verification_cmd': self.has_verification_method(code),
            # 動作確認のコマンドが提供されているか
            
            'error_handling': self.has_error_handling(code),
            # エラー処理（try-catchなど）があるか
            
            'rollback_plan': self.has_rollback_procedure(code)
            # 元に戻す手順が書かれているか
        }
        return all(checks.values())  # 全てTrueならTrue、1つでもFalseならFalse
```

**用語解説**:
- **validate**: 検証する（正しいかチェックする）
- **syntax**: 構文（プログラミング言語の文法）
- **context**: コンテキスト（前後関係、必要な情報）
- **error handling**: エラー処理（予期しない状況への対処）
- **rollback**: ロールバック（変更を元に戻すこと）

---

## コードサンプル検証例（1/2）

**robots.txt サンプル**:

- ✓ User-agent指定正しい
  - `User-agent: GPTBot`（クローラーの種類を指定）
- ✓ Crawl-delay整数値
  - `Crawl-delay: 1`（1秒間隔で巡回、負荷軽減）
- ✓ Disallow/Allow相対パス
  - `Disallow: /admin/`（/admin/配下は拒否）
  - `Allow: /products/`（/products/配下は許可）
- ✓ Sitemap絶対URL
  - `Sitemap: https://example.com/sitemap.xml`（完全なURL）
- ✓ 構文エラーなし
  - スペルミスや書式エラーがない

**用語解説**:
- **User-agent**: ユーザーエージェント（ブラウザやクローラーの識別名）
- **Crawl-delay**: クロール間隔（秒単位）
- **Disallow**: 禁止（このパスは巡回させない）
- **Allow**: 許可（このパスは巡回を許可）
- **絶対URL**: ドメインから書く完全なURL（相対URLは不可）

---

## コードサンプル検証例（2/2）

**JSON-LD サンプル**:

- ✓ @context定義
  - `"@context": "https://schema.org"`（語彙の定義元）
- ✓ @type指定
  - `"@type": "Product"`（このデータは商品情報）
- ✓ 必須プロパティ全て存在
  - `name`, `image`, `offers`など必須項目が揃っている
- ✓ Schema.org vocabulary準拠
  - Schema.orgで定義された語彙のみ使用
- ✓ JSON構文有効
  - カンマ・括弧・引用符が正しい

**用語解説**:
- **JSON-LD**: JSON for Linked Data（構造化データ形式）
- **@context**: コンテキスト（語彙の定義場所）
- **@type**: タイプ（データの種類）
- **vocabulary**: ボキャブラリー（使用可能な語彙の集合）
- **プロパティ**: 属性（nameやpriceなど）

**検証ツール**: Schema Markup Validator（構造化データ検証ツール）

---

## 検証コマンド自動生成

```python
def generate_verification_commands(artifact_type):  # ファイルタイプを受け取る
    # commandsは辞書型（ファイルタイプ: コマンドリストのペア）
    commands = {
        'robots.txt': [  # robots.txtの検証コマンド
            'curl -I https://example.com/robots.txt',
            # curl: HTTPリクエストを送るコマンド
            # -I: ヘッダー情報のみ取得（本文は不要）
            'robots.txt構文チェッカー利用'
            # Web上のバリデーターツールで確認
        ],
        'sitemap.xml': [  # XMLサイトマップの検証コマンド
            'xmllint --noout sitemap.xml',
            # xmllint: XML構文チェックツール
            # --noout: エラーがなければ何も出力しない
            'gunzip -t sitemap.xml.gz'
            # gunzip -t: gzip圧縮ファイルの整合性テスト
        ],
        'json-ld': [  # JSON-LDの検証
            'Schema Markup Validator',
            # Googleの構造化データテストツール
            'Google Rich Results Test'
            # リッチリザルト表示テスト
        ],
        'openapi': [  # OpenAPI仕様の検証
            'Swagger Editor validation'
            # Swagger Editor（オンラインエディタ）で検証
        ]
    }
    return commands.get(artifact_type, [])  # 該当するコマンドリストを返す
    # get(): 辞書からキーで値を取得（存在しなければ[]を返す）
```

**用語解説**:
- **artifact**: 成果物（ファイルやコード）
- **curl**: URL転送ツール（HTTPリクエスト送信）
- **xmllint**: XMLファイルの検証ツール
- **gunzip**: gzip形式の圧縮ファイルを展開するツール
- **Validator**: バリデータ（検証ツール）

---

<!-- _class: lead -->
# Phase 5
## 日本固有要件への適応

**「グローバル → 日本対応」フェーズ**

---

## Phase 5の目的

**解説**:
- 日本の法律に準拠
- 日本語の文例を追加
- 日本固有の慣行を反映

**例え**:
海外の料理レシピを日本の食材と調味料で
作れるようにアレンジする

---

## 日本法務情報の取得戦略

**4つの主要法規制**:

1. **APPI**（個人情報保護法）
   - Act on the Protection of Personal Information
   - 個人情報の取り扱いルールを定めた法律
   - 情報源: 個人情報保護委員会公式サイト

2. **P-Mark**（プライバシーマーク）
   - 個人情報保護の第三者認証制度
   - JIS Q 15001:2017に基づく
   - 情報源: JIPDEC（日本情報経済社会推進協会）

3. **著作権法30条の4**（AI学習例外）
   - 2019年施行の改正著作権法
   - AI学習目的の複製を例外的に許可
   - 情報源: 文化庁公式見解

4. **TBA**（電気通信事業法）
   - Telecommunications Business Act
   - 2023年6月施行改正（Cookie規制導入）
   - 第三者へのCookie送信時の同意取得義務
   - 情報源: 総務省公式サイト

**用語解説**:
- **個人情報**: 特定の個人を識別できる情報
- **第三者認証**: 外部の専門機関による認証
- **著作権**: 創作物の権利（コピーや改変の権利）
- **Cookie**: Webブラウザに保存される小さなデータファイル

---

## グローバル → 日本適応

```python
def adapt_to_japan_context(global_best_practice):  # グローバル標準を受け取る
    # 1. 法的制約の追加
    if requires_gdpr_consent(global_best_practice):  # GDPR同意が必要か？
        add_appi_requirements()  # 日本のAPPI要件を追加
        # GDPR（EU一般データ保護規則）→ APPI（日本）への変換
    
    # 2. 日本語文例の追加
    if has_english_examples(global_best_practice):  # 英語例があるか？
        add_japanese_examples()  # 日本語の例を追加
        # 単なる翻訳ではなく、日本の商習慣に合わせた例文
    
    # 3. P-Mark等認証への言及
    if involves_privacy(global_best_practice):  # プライバシー関連か？
        add_pmark_guidance()  # P-Mark（日本の認証制度）の説明を追加
    
    # 4. 日本固有慣行の反映
    if relates_to_ecommerce(global_best_practice):  # EC関連か？
        add_japanese_ec_practices()  # 日本のEC業界の慣行を反映
        # 例: 代引き決済、コンビニ受取などの記載
```

**用語解説**:
- **GDPR**: General Data Protection Regulation（EU一般データ保護規則）
- **best practice**: ベストプラクティス（最良の方法）
- **context**: コンテキスト（文脈、状況）
- **consent**: 同意（ユーザーの許可）
- **privacy**: プライバシー（個人の私的領域）
- **慣行**: 業界で一般的に行われている方法

---

<!-- _class: lead -->
# Phase 6
## 品質保証とセルフレビュー

**「間違いがないか確認」フェーズ**

---

## Phase 6の目的

**解説**:
- 必須項目の漏れチェック
- よくあるミスを検出
- 情報の最新性を確認

**例え**:
提出前のレポートを
チェックリストで確認する

---

## 完全性チェックマトリクス

**必須要件の確認**:

- [✓] タイトルに発行日
- [✓] 要約5行以内
- [✓] 実装チェックリスト
- [✓] 8領域全カバー
- [✓] 参照実装6種
- [✓] KPI/テストプロンプト
- [✓] 法務注意点
- [✓] 付録

---

## アンチパターン検出

```python
class QualityAssurance:  # 品質保証クラス
    def check_anti_patterns(self, content):  # コンテンツを検査
        errors = []  # エラーリスト（空で初期化）
        
        # AP1: 古い情報のチェック
        if contains_outdated_info(content):  # 古い情報が含まれているか
            errors.append("2024年以前の情報が混入")
            # append(): リストに要素を追加
        
        # AP2: 未検証コードのチェック
        if has_unverified_code(content):  # 検証されていないコード？
            errors.append("検証方法のないコードサンプル")
            # 動作確認の方法が書かれていない
        
        # AP3: 曖昧な指示のチェック
        if has_vague_instructions(content):  # 曖昧な表現？
            errors.append("「適宜」「必要に応じて」等の曖昧表現")
            # 具体的にどうすればいいか分からない表現
        
        return errors  # 検出されたエラーのリストを返す
        # 空リスト[]ならエラーなし、要素があればエラーあり
```

**用語解説**:
- **Anti-pattern**: アンチパターン（避けるべき悪い書き方）
- **Quality Assurance (QA)**: 品質保証（製品の品質を確保する活動）
- **outdated**: 時代遅れの、古くなった
- **unverified**: 未検証の、確認されていない
- **vague**: 曖昧な、ぼんやりした
- **instruction**: 指示、手順

---

<!-- _class: lead -->
# Phase 7
## メタ認知と改善ループ

**「これで本当に良いか」を考えるフェーズ**

---

## 評価プロセス

**4つの質問**:

1. **即実装できるか？** → YES
2. **来年も有効か？** → 一部変動
3. **法的リスクないか？** → YES
4. **大規模でも使えるか？** → YES

---

## 未解決課題の明示

**Known Limitations**:

1. **UA偽装対策の限界**
   - 完全防御は不可能
   
2. **LLM内部指標の不透明性**
   - 内部ランキング非公開

3. **robots.txt無視クローラー**
   - 技術的防御に限界

---

<!-- _class: lead -->
# Phase 8
## 出力フォーマット最適化

**「読みやすく整える」フェーズ**

---

## Markdown構造設計

**階層の基本**:

```markdown
# Level 1: タイトル（文書全体で1個のみ）
## Level 2: 章（Chapter、8個程度）
### Level 3: 節（Section、各章3-5個）
#### Level 4: 詳細（必要な場合のみ）

コードブロック:
```言語名
コードをここに書く
```

リスト:
- 箇条書き項目1
- 箇条書き項目2

強調:
**太字** または *斜体*
`インラインコード`
```

**用語解説**:
- **Markdown**: マークダウン（軽量マークアップ言語）
- **見出し**: `#`の数で階層を表現（`#`が1個=レベル1）
- **コードブロック**: ` ``` `で囲んだ領域（コードを表示）
- **インラインコード**: 本文中の`コード`（バッククォートで囲む）
- **箇条書き**: `-`や`*`で始まる行
- **強調**: `**`で太字、`*`で斜体

**ルール**: 
- Level 1は文書の冒頭に1つだけ
- Level 2で大きく区切る
- 階層を飛ばさない（Level 2の次は必ずLevel 3）

---

## 視認性の最適化

```python
class DocumentFormatter:  # ドキュメント整形クラス
    def optimize_readability(self, content):  # 読みやすさを最適化
        # 1. セクション長の制御
        max_section_lines = 50  # 1セクション最大50行
        # 画面2-3スクロールで読める長さに制限
        
        # 2. コードブロックの適切な配置
        code_after_explanation = True  # 説明の後にコードを配置
        # 先に何のコードか説明してから、実際のコードを示す
        
        # 3. 視覚的階層の明確化
        use_horizontal_rules = True  # 水平線（---）を使用
        # セクション間の区切りを視覚的に分かりやすく
        
        # 4. 重要情報の強調
        highlight_critical_info = True  # 重要情報をハイライト
        # 太字、色付け、ボックスなどで強調
        
        # 5. 実装例の前後に説明
        sandwich_structure = True  # サンドイッチ構造
        # 説明 → コード → 検証方法の3層構造
```

**用語解説**:
- **Formatter**: フォーマッター（書式整形ツール）
- **readability**: 可読性（読みやすさ）
- **optimize**: 最適化する（より良い状態にする）
- **section**: セクション（文書の区切り）
- **horizontal rule**: 水平線（`---`で引く線）
- **highlight**: ハイライト（強調表示）
- **critical**: 重要な、決定的な
- **sandwich structure**: サンドイッチ構造（挟み込む形）

---

<!-- _class: lead -->
# Phase 9
## 継続的改善の仕組み

**「育て続ける」フェーズ**

---

## Phase 9の目的

**解説**:
- フィードバックを収集
- 定期的に更新
- バージョン管理

**例え**:
ソフトウェアアップデートのように、
定期的に改善版をリリース

---

## フィードバックループ設計

```
Week 1: 初版リリース
  ↓
Week 2-4: フィードバック収集
  ↓
Month 2: v1.1リリース
  ↓
Quarter 1: v2.0リリース
```

****: 
完璧を待たず、まずリリース

---

## バージョン管理戦略

**命名規則（Semantic Versioning の変形）**:

```
日付ベースのバージョニング:
YYYY-MM-DD形式

2025-10-10  ← 初版リリース（Initial Release）
2025-11-10  ← 月次小改訂（Minor Update）
2026-01-10  ← 四半期大改訂（Major Update）
2026-04-10  ← 年次全面見直し（Complete Review）
```

**変更管理ファイル**:

```markdown
CHANGELOG.md（変更履歴ファイル）:
## [2025-11-10] - 2025年11月10日
### Added（追加）
- 新しいAIクローラー3種を追加

### Changed（変更）
- robots.txt設定例を最新版に更新

### Deprecated（非推奨）
- 旧バージョンのOpenAPI 3.0例を削除予定

### Removed（削除）
- 古くなった2024年の統計データを削除

### Fixed（修正）
- サンプルコードの構文エラーを修正

### Security（セキュリティ）
- 脆弱性のある依存関係を更新
```

**用語解説**:
- **Versioning**: バージョニング（版管理）
- **Semantic**: セマンティック（意味論的な）
- **Initial Release**: 初版リリース（最初の公開版）
- **Minor Update**: マイナーアップデート（小さな更新）
- **Major Update**: メジャーアップデート（大きな変更）
- **CHANGELOG**: チェンジログ（変更履歴）
- **Deprecated**: 非推奨（将来削除予定）

---

<!-- _class: lead -->
# Appendix A
## プロンプトエンジニアリング教訓

---

## 効果的だった指示

**Good Practices**:

- ✓ 「コピペで通ること」
- ✓ 「検証コマンド付与」
- ✓ 「ロールバック手順」
- ✓ 「一次情報優先」
- ✓ 「日付明記」

**Key Learning**: 
具体的・検証可能・文脈明確

---

## 改善余地のあった指示

| 指示 | 問題 | 改善案 |
|-----|------|--------|
| 15分で終了 | 深度制限 | 最大深度確保 |
| 全サンプル詳細 | 冗長性 | 初出のみ詳細 |
| 相反情報併記 | 判断負担 | 推奨案提示 |

****: 
制約と品質のバランス

---

<!-- _class: lead -->
# Appendix B
## AI思考の限界と人間判断の必要性

---

## AIが得意な領域

**5つの得意分野**:

✓ 大量情報の構造化
✓ パターン認識と分類
✓ 公開情報の横断検索
✓ コード生成と構文検証
✓ 一貫性のある文書作成

****: 
AIは「情報の整理屋さん」

---

## 人間判断が必要な領域

**5つの不得意分野**:

✗ 組織固有の優先順位
✗ リスク許容度の判断
✗ 予算・工数の制約調整
✗ 非公開情報の判断
✗ 倫理的グレーゾーン

****: 
最終判断は必ず人間が行う

---

## AI×人間の協調モデル

**理想的な分担**:

```
人間 (20%)
├── 戦略決定
├── 最終判断
└── リスク評価

AI (80%)
├── 情報収集
├── 構造化
└── 草案作成
```

**推奨**: AIで8割、人間で完成へ

---

<!-- _class: lead -->
# まとめ

---

## 8つのエッセンス

1. **階層的制約理解**: 上位→全体、下位→部分
2. **3層リサーチ**: 公式→業界→問題
3. **信頼性判断**: 公式10点、個人5点
4. **依存関係**: 実装順序の最適化
5. **品質6項目**: 構文・完全性・検証等
6. **日本適応**: グローバル+日本法務
7. **メタ認知**: 自己評価・限界明示
8. **継続改善**: 四半期レビュー

---

## エンジニアへの5つのアドバイス

1. **プロンプトは仕様書**
   → 曖昧さを排除

2. **階層的制約を意識**
   → 上位制約は全体に適用

3. **一次情報への執着**
   → 公式ドキュメント必須

4. **完璧を求めない**
   → 80%でリリース、改善継続

5. **AI×人間協調**
   → AIは道具、判断は人間

---

## 実践的Tips（詳細解説）

**プロンプト設計**:
- ❌ 「〜してください」（曖昧）
- ✅ 「〜の条件で作成」（具体的）
  - 条件: ファイル形式、文字数、言語など
  - 例: 「Markdown形式、5000文字以内、日本語で作成」

**情報検証**:
- 必ず公式サイト確認
  - 公式サイト: 企業や政府の正式なウェブサイト
- 日付・バージョン記録
  - いつの情報か、どのバージョンかをメモ
- 複数ソースで検証
  - 1つの情報源だけでなく、2-3個で確認

**品質保証**:
- コードは実行テスト
  - 実行テスト: 実際に動かして確認すること
- エッジケース検討
  - エッジケース: 極端な条件（空文字、最大値など）
- ロールバック計画
  - ロールバック: 元の状態に戻す手順

**用語解説**:
- **プロンプト**: AIへの指示文
- **検証**: 正しいか確認すること（Verification）
- **ソース**: 情報源（Source）
- **品質保証**: 製品の品質を確保すること（QA）

---

## 参考リソース（）

**プロンプトエンジニアリング**:
- Anthropic Prompt Engineering
- OpenAI Best Practices

**基礎知識**:
- リーダブルコード（書籍）
- プログラマが知るべき97のこと（書籍）

**実践**:
- GitHub Examples
- Stack Overflow

---

## 学習の進め方（へ）

**ステップ1**: 小さく始める
- 簡単なプロンプトから

**ステップ2**: 実際に試す
- コピペして動かす

**ステップ3**: 少しずつ改変
- 自分のケースに適用

**ステップ4**: 失敗から学ぶ
- エラーは成長の機会
