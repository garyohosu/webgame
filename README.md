# Claude Code 指示書パック（1日1スマホゲーム × GitHub Pages）

目的：毎日1個、スマホ（縦画面・親指操作）向けミニゲームを `index.html` 1ファイル完結で作成し、GitHub Pagesで公開する。
データベース無し。状態保存は localStorage のみ（ハイスコアなど）。

## 0. このパックの使い方（最短）
1. このZIPを展開して、あなたのリポジトリに入れる
2. Claude Codeに `INSTRUCTIONS.md` を渡して実行
3. 毎日 `games/YYYY-MM-DD-<slug>/` を1個追加し、ルート `index.html` にリンクを1行足して push

## 1. 制約（絶対）
- スマホ縦画面前提（幅 360〜430px 想定）。スクロール無し（1画面完結）
- 操作はタップ中心（タップのみ or タップ＋長押しまで）。スワイプは原則禁止
- 1ゲーム = 1メカニクス
- 1分で完結（60秒タイマー or 3回ミス終了など）
- 外部依存なし（CDN/外部JS/外部CSS 不使用）。`index.html` 単体で完結
- DBなし：保存は localStorage のみ。個人情報を保存しない
- 権利物禁止：既存作品の無断切り抜き・キャラ・音源・画像の流用は禁止

## 2. リポジトリ最小構成
/index.html
/games/YYYY-MM-DD-<slug>/
  index.html
  SPEC.md
  QA.md
/.github/workflows/pages.yml

## 3. 今日の作業（毎日これだけ）
- `games/2026-03-03-<slug>/SPEC.md` を作る（仕様）
- `games/2026-03-03-<slug>/index.html` を作る（実装）
- `games/2026-03-03-<slug>/QA.md` を作る（チェック結果）
- ルート `index.html` にカード1個追加（リンク）

## 4. GitHub Pages（Actions）メモ
`pages.yml` はこのZIPに同梱。
リポジトリ側で Settings → Pages → Build and deployment → Source を GitHub Actions にする。
