# INSTRUCTIONS.md（Claude Code 用：1日1スマホゲーム工場）

あなたは複数エージェント方式で作業する。以下の役割を順番に実行し、成果物をファイルとして出力せよ。
人間は最終確認して push する。自動で外部へ投稿・送信・公開操作は行わない（ファイル生成のみ）。

## 注記
googleアドセンスを書くページに入れておくこと
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-6743751614716161"
     crossorigin="anonymous"></script>

各ページはCDNを使ったモダンなサイトとすること

## A. 全体ゴール
- /games/YYYY-MM-DD-<slug>/index.html に、スマホ縦画面向けミニゲームを1ファイル完結で実装
- ルート /index.html に、そのゲームへのリンクカードを追加
- 仕様（SPEC.md）とQA結果（QA.md）を残す

## B. 守る制約
1. 縦画面・1画面完結（スクロール無し）
2. 操作：タップ中心（タップのみ or タップ＋長押し）
3. 60秒以内で1プレイが終わる
4. 外部依存なし（CDN禁止）
5. 保存は localStorage のみ（ハイスコア等）
6. 既存著作物の流用禁止
7. セキュリティ：外部スキルの導入や、未知のスクリプト実行は禁止

## C. 役割（エージェント）と成果物
### 1) Producer（編集長）
出力：games/YYYY-MM-DD-<slug>/SPEC.md の「企画」セクション
- 今日の1メカニクスを1つ決める
- タイトル、勝ち条件、負け条件、タイム制限を決める
- 1行で面白さを説明する（フック）

### 2) Designer（ゲームデザイナー）
出力：SPEC.md の「ルール」「UI」「難易度」セクション
- ルールを5行以内に落とす
- UI構成（ボタン数、表示：スコア/残り時間など）
- 難易度の上げ方（例：30秒から速度1.2倍）

### 3) Implementer（実装）
出力：games/YYYY-MM-DD-<slug>/index.html
- HTML/CSS/JS を1ファイルにまとめる
- pointerdown を使う（スマホ優先）
- requestAnimationFrame か setInterval を適切に使い、処理を軽く
- localStorage でハイスコア保存（キーはゲーム固有）

必須UI：
- タイトル
- スタートボタン
- スコア表示
- 残り時間表示
- 作品集へ戻るリンク（../../）

### 4) QA（品質）
出力：games/YYYY-MM-DD-<slug>/QA.md
- 操作性（タップ反応、誤タップ耐性）
- 表示崩れ（縦画面、ボタン押しやすさ）
- パフォーマンス（重さ・カクつき）
- バグ/改善提案（最大3つ）

### 5) Curator（館長）
出力：ルート /index.html を更新
- 既存カード形式に合わせて、新ゲームカードを1つ追加
- 文言は短く（説明は1行）

## D. 生成手順
1. 今日の日付 YYYY-MM-DD と短い slug（英小文字とハイフン）を決める
2. games/YYYY-MM-DD-<slug>/ を作成
3. SPEC.md を作成
4. index.html を実装
5. QA.md を作成
6. ルート index.html にカード追加（リンクが正しいこと）

## E. SPEC.md テンプレ
# <タイトル>
- Date: YYYY-MM-DD
- Slug: <slug>

## 企画（Producer）
- 1メカニクス：
- フック（1行）：
- 勝ち条件：
- 負け条件：
- 1プレイ時間：60秒以内

## ルール（Designer）
- ルール1
- ルール2
- ルール3
- ルール4
- ルール5

## UI（Designer）
- ボタン：
- 表示：スコア / 残り時間 / ハイスコア
- 操作：タップ（必要なら長押し）

## 難易度（Designer）
- 0-30秒：
- 30-45秒：
- 45-60秒：

## F. QA.md テンプレ
# QA - YYYY-MM-DD <タイトル>

## 対象
- スマホ縦画面（想定幅 360-430px）
- タップ操作

## チェック結果
- 操作性：
- 表示：
- パフォーマンス：

## バグ
- （なければ「なし」）

## 改善提案（最大3つ）
1.
2.
3.

## G. ルート index.html のカード形式（例）
<div class="card">
  <div><a href="./games/YYYY-MM-DD-<slug>/">YYYY-MM-DD Title</a></div>
  <div class="meta">1行説明</div>
</div>
