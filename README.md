# Daily Game Factory

1日1個、スマホ向けミニゲームを作り続けるプロジェクト。
GitHub Pages で公開中 → **https://garyohosu.github.io/webgame/**

---

## 🤖 Claude Code（AI）への指示

> このセクションは Claude Code が読む想定です。毎日の作業はここから始めてください。

### 毎日の作業手順

1. `INSTRUCTIONS.md` を読み、5つの役割（Producer → Designer → Implementer → QA → Curator）を順番に実行する
2. 今日の日付（`YYYY-MM-DD`）と slug（英小文字・ハイフン）を決める
3. 以下のファイルを生成する：
   ```
   games/YYYY-MM-DD-<slug>/SPEC.md       ← 企画・ルール・UI・難易度
   games/YYYY-MM-DD-<slug>/index.html    ← ゲーム本体（1ファイル完結）
   games/YYYY-MM-DD-<slug>/QA.md         ← QAレポート
   ```
4. ルートの `index.html` にゲームカードを1枚追加する（`.card-list` の中、最新が一番上）
5. `CHANGELOG.md` に1行追記する
6. `git add`・`git commit`・`git push` する（人間の確認後）

### ゲーム実装の必須要件

| 項目 | 内容 |
|------|------|
| 画面 | 縦画面・1画面完結（スクロールなし） |
| 操作 | `pointerdown` 使用（タップ中心） |
| 時間 | 60秒以内で1プレイ完結 |
| 外部依存 | ゲームロジックは CDN 禁止・自己完結 |
| 保存 | `localStorage` のみ（キーはゲーム固有） |
| アニメ | `requestAnimationFrame` または `setInterval` |
| 必須UI | タイトル・スタートボタン・スコア・残り時間・戻るリンク（`../../`） |
| 広告 | Google AdSense スクリプトをページに含める（`INSTRUCTIONS.md` 参照） |

### ルート index.html カードの追加形式

```html
<!-- カードは .card-list の中に追記。最新ゲームを一番上に -->
<a class="card reveal" href="./games/YYYY-MM-DD-<slug>/">
  <div class="card-inner">
    <div class="card-icon">🎮</div>  <!-- ゲームに合った絵文字 -->
    <div class="card-body">
      <div class="card-date">YYYY-MM-DD</div>
      <div class="card-title">タイトル</div>
      <div class="card-meta">1行の説明文。</div>
    </div>
    <div class="card-arrow">›</div>
  </div>
</a>
```

### CHANGELOG.md への追記形式

```
## YYYY-MM-DD — タイトル (`slug`)
- メカニクス・特徴を1〜2行で。
```

---

## 📁 リポジトリ構成

```
webgame/
├── index.html                        # トップページ（ゲーム一覧）
├── INSTRUCTIONS.md                   # エージェント詳細指示書
├── README.md                         # このファイル
├── CHANGELOG.md                      # 更新履歴
├── .gitignore
├── .github/
│   └── workflows/
│       └── pages.yml                 # GitHub Pages 自動デプロイ
└── games/
    └── YYYY-MM-DD-<slug>/
        ├── index.html                # ゲーム本体
        ├── SPEC.md                   # 仕様書
        └── QA.md                    # QAレポート
```

---

## ⚙️ GitHub Pages セットアップ

Settings → Pages → Source → **GitHub Actions** を選択。
`.github/workflows/pages.yml` が自動デプロイを行う。

---

## 📜 ライセンス

各ゲームは既存著作物を流用しない完全オリジナル実装。
