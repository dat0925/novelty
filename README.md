# ノベルティカード ジェネレーター

MEOサービス付帯の「Googleクチコミ募集ショップカード」をAIで自動生成するWebツールです。

## 使い方

1. [このページを開く](https://dat0925.github.io/novelty/)
2. **Claude APIキー**を入力（`sk-ant-api...` で始まるキー）
3. 店舗情報・デザイン設定をフォームで入力
4. 「AIでデザイン生成」ボタンを押す
5. プレビューを確認して「印刷用PDF保存」でPDFダウンロード
6. PDFを印刷会社（コスモプリンツ等）に入稿

## APIキーについて

### 選択肢A：都度入力方式（現在の実装）
- 各自がAnthropicのAPIキーを入力して使用
- キーはブラウザのsessionStorageに一時保存（タブを閉じると消える）
- **メリット**: コストを個人単位で管理できる、バックエンド不要
- **デメリット**: 毎回入力が必要（sessionStorage保存で軽減）

### APIキーの取得方法
1. https://console.anthropic.com/ にアクセス
2. アカウント作成・ログイン
3. API Keys → Create Key
4. 生成されたキーをコピーして本ツールに貼り付け

### コスト目安
- Claude claude-opus-4-5 使用: 1回の生成で約0.03〜0.08ドル（3〜6パターン）
- 月10回利用で約100円程度

### 将来の選択肢B：共有APIキー方式
バックエンドサーバー（Vercel / Cloudflare Workers）を設置してAPIキーを格納。
全員がキー入力なしで使えるようになります。
費用: サーバー無料枠 + APIコスト（月数百円〜）

## 仕様

- カードサイズ: 名刺縦型 55mm × 91mm
- 出力: 表・裏2面のHTMLプレビュー → PDF
- AI: Claude API (claude-opus-4-5)
- PDF生成: jsPDF + html2canvas（ブラウザ完結）

## 開発

```bash
# ローカル確認
npx serve .
# → http://localhost:3000
```

GitHub Pagesで自動公開されます（mainブランチpush時）。
