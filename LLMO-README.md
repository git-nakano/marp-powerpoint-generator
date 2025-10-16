# LLMO実装仕様書 - 使い方ガイド

## 📦 ファイル構成

- `llmo-implementation-spec.md` - LLMO実装仕様書（Marp形式、40スライド）
- `llmo-tech-docs.css` - カスタムテーマCSS（可視性最適化版）
- `README.md` - このファイル

## 🚀 クイックスタート

### 1. Marp拡張機能のインストール（VS Code）

```bash
# VS Code拡張機能検索で "Marp for VS Code" をインストール
```

または、[VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) からインストール。

### 2. CSSファイルの配置

`llmo-tech-docs.css` を以下のいずれかに配置：

**方法A：プロジェクトローカル（推奨）**
```
project-root/
├── .vscode/
│   └── settings.json  ← 設定ファイル
├── themes/
│   └── llmo-tech-docs.css  ← ここに配置
└── llmo-implementation-spec.md
```

`.vscode/settings.json` に以下を追加：
```json
{
  "markdown.marp.themes": [
    "./themes/llmo-tech-docs.css"
  ]
}
```

**方法B：グローバル設定**
```
C:\Users\[ユーザー名]\.marp\themes\llmo-tech-docs.css
```

### 3. プレビュー表示

1. VS Codeで `llmo-implementation-spec.md` を開く
2. `Ctrl + Shift + V` でプレビュー表示
3. 右上の「Marpプレビュー」ボタンをクリック

## 📤 エクスポート方法

### PDF出力（推奨）

#### VS Code内から
1. Marpプレビューを開く
2. 右上の「Export slide deck」ボタン
3. 「PDF」を選択
4. 保存先を指定

#### Marp CLI使用
```bash
# Marp CLIインストール
npm install -g @marp-team/marp-cli

# PDF出力
marp llmo-implementation-spec.md --theme themes/llmo-tech-docs.css --pdf --allow-local-files

# HTML出力（スタンドアロン）
marp llmo-implementation-spec.md --theme themes/llmo-tech-docs.css --html

# PowerPoint出力
marp llmo-implementation-spec.md --theme themes/llmo-tech-docs.css --pptx
```

### HTML出力（ブラウザ表示用）

```bash
marp llmo-implementation-spec.md --theme themes/llmo-tech-docs.css --html -o output.html
```

生成されたHTMLファイルはブラウザで直接開けます。

## 🎨 テーマの特徴（可視性向上版）

### 改善ポイント

#### 1. **フォント・行間の最適化**
- 本文サイズ：22px（読みやすさ重視）
- 行間：1.7（詰まり感を解消）
- 文字間隔：見出しに適度なletter-spacing

#### 2. **コードブロックの視認性強化**
- インラインコード：明るい背景 + 赤系テキスト + 境界線
- コードブロック：影追加 + 左ボーダー + パディング増
- シンタックスハイライト対応準備

#### 3. **テーブルの可読性向上**
- ホバー時の背景色変化（インタラクティブ）
- 影追加で立体感
- ヘッダー色を確実に表示（!important）
- セル内パディング増加

#### 4. **チェックリストの視認性**
- チェックボックスサイズ拡大（18px）
- チェック済みアイテムは取り消し線 + 薄色
- アクセントカラー（緑）適用

#### 5. **章区切りの明確化**
- `<!-- _class: chapter -->` で章タイトルページ
- グラデーション背景（青系）
- 大きな見出し（56px）

#### 6. **警告・情報ボックス**
- 引用ブロックで色分け：
  - ⚠️ 警告（オレンジ）
  - ✅ 成功（緑）
  - ❌ エラー（赤）
- 影追加で視認性向上

#### 7. **ページ番号の改善**
- 背景付き + 境界線
- 視認性の高い配置

#### 8. **アクセシビリティ**
- ハイコントラストモード対応
- フォーカス時の視認性向上
- 印刷最適化（改ページ制御）

## 📝 カスタマイズ方法

### 色の変更

`llmo-tech-docs.css` の `:root` セクションを編集：

```css
:root {
  --color-primary: #1e3a8a; /* 深い青 → お好みの色 */
  --color-secondary: #3b82f6; /* 明るい青 */
  --color-accent: #60a5fa; /* アクセント青 */
  /* ... 他の色も変更可能 */
}
```

### フォントサイズの調整

```css
section {
  font-size: 22px; /* ← この値を変更 */
}
```

### 2カラムレイアウトの使用

特定のスライドを2カラムにする場合：

```markdown
---
<!-- _class: columns -->

## 見出し（全幅表示）

### 左カラム
内容...

### 右カラム
内容...
```

## 🔍 トラブルシューティング

### Q1: テーマが適用されない

**原因：** CSSファイルのパスが正しくない

**解決策：**
1. `.vscode/settings.json` のパスを確認
2. 相対パスが正しいか確認（`./themes/llmo-tech-docs.css`）
3. VS Codeを再起動

### Q2: PDF出力で日本語が文字化け

**原因：** フォント設定の問題

**解決策：**
```bash
# --pdf-notesオプションを追加
marp llmo-implementation-spec.md --theme themes/llmo-tech-docs.css --pdf --allow-local-files --pdf-notes
```

または、CSSの `font-family` に日本語フォントを追加：
```css
font-family: "Yu Gothic", "Meiryo", "Hiragino Sans", sans-serif;
```

### Q3: コードブロックの色が表示されない

**原因：** シンタックスハイライトは言語指定が必要

**解決策：**
Markdownで言語を指定：
````markdown
```javascript
const example = "hello";
```
````

### Q4: チェックボックスが表示されない

**原因：** Marpの設定が無効

**解決策：**
`.vscode/settings.json` に追加：
```json
{
  "markdown.marp.enableHtml": true
}
```

## 📚 参考リンク

- [Marp公式ドキュメント](https://marpit.marp.app/)
- [Marp CLI](https://github.com/marp-team/marp-cli)
- [Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode)

## 🛠️ 推奨ワークフロー

1. **編集** - VS Codeでリアルタイムプレビュー確認
2. **レビュー** - PDFエクスポートして開発チームと共有
3. **プレゼン** - HTMLエクスポートしてブラウザ全画面表示
4. **配布** - PDF版を最終成果物として配布

## 📊 パフォーマンスTIPS

- 画像は適度に圧縮（推奨：最大1920px幅）
- スライド数が多い場合は章ごとに分割も検討
- PDF出力時は `--allow-local-files` を忘れずに

## ✅ チェックリスト

- [ ] Marp for VS Code インストール済み
- [ ] CSSファイルをthemesフォルダに配置
- [ ] .vscode/settings.json 設定完了
- [ ] プレビュー表示確認
- [ ] PDF出力テスト完了
- [ ] 開発チームと共有

---

**作成日：** 2025-10-15  
**バージョン：** 1.0  
**お問い合わせ：** プロジェクトSlack #web-projects
