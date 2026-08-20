# pinterest-saas-affiliate

海外SaaSアフィリエイト × Pinterest比較記事による副業プロジェクト。

スロースタート方針：自動化を先に作り込まず、1〜2商材で手動検証してから横展開する。

## 決定事項

- **対象ジャンル**: プロジェクト管理SaaS（日本人参入者が少ないジャンルとして選定）
- **収益モデル**: 海外SaaSのアフィリエイト/リファラルプログラム。継続報酬型（recurring commission）かどうかを商材ごとに規約で必ず確認する
- **コンテンツ**: Reddit・英語YouTubeレビューをリサーチし、ネイティブトーンの英語比較記事を作成 → 記事テーマを基にPinterestピンを設計
- **投稿基盤**: X（Twitter）ではなくPinterestに集中。X Developer APIクレジットは保留中（今回は使わない）
- **自動化基盤**: VPSは使わず、GitHub Actionsのスケジュール実行（cron）で投稿スクリプトを動かす方針
- **記事の質**: AI丸投げにせず、Grammarly等でのネイティブチェックを必ず一段階挟む
- **記事の公開先**: Medium（無料プラン）。アフィリエイトリンクは許可されているが開示必須（Medium規約・FTC準拠）。記事末尾に開示文を必ず入れる
- **対象SaaS**: Teamwork.com（アカウント作成済み、リファラルリンク発行済み・`.env`の`TEAMWORK_REFERRAL_LINK`）、Paymo（アカウント作成済み・アフィリエイト申請済み、審査待ち）

## フォルダ構成

```
research/           # Reddit/YouTubeリサーチ結果（{saas_name}/ ごと）
content/            # 比較記事の下書き
pins/
  copy/              # ピンのコピー文言
  images/            # ピン画像（Canva/テンプレート合成、git管理外）
scripts/
  research_batch.py   # リサーチのバッチ処理（後回しでよい）
  draft_article.py     # 記事執筆支援
  generate_pin_copy.py # ピンコピー生成
  post_pinterest.py    # Pinterest API投稿（型が固まってから実装）
data/
  schedule_queue.csv   # 投稿予定管理
.github/workflows/     # GitHub Actionsのスケジュール実行定義
.env                    # APIキー（.gitignore対象、.env.exampleを参照して作成）
```

## タスクロードマップ（優先順）

1. プロジェクト環境をセットアップ — フォルダ構成を作成し、Git管理下に置く。`.env`と`.gitignore`を用意
2. 対象SaaSを1〜2つに絞る — アフィリエイトプログラムの規約を実際に読み、継続報酬型かどうか確認する
3. Reddit・YouTubeリサーチを実行 — Web検索でユーザーの本音の不満・比較ポイントを収集し `research/{saas_name}/` にまとめる
4. 比較記事の下書きを作成 — リサーチ結果を基に英語記事を執筆。ネイティブチェックを一段階挟む
5. Pinterestビジネスアカウントを整備 — 個人アカウントから切り替え、並行してPinterest API v5の利用申請を進める（審査に時間がかかるため早めに着手）
6. ピンを試験的に手動投稿（5〜10枚） — 自動化前に手動で投稿し反応を見る
7. 反応を計測し、型を検証 — クリック率・記事流入・アフィリエイトリンククリックを数週間観察。反応が薄ければ2に戻る
8. Pinterest投稿の自動化スクリプトを構築 — 型が固まってから `post_pinterest.py` を実装し、GitHub Actionsでスケジュール実行する
9. リサーチ自動化とジャンル横展開 — 成果が出た型を他ジャンルにも展開できるよう `research_batch.py` を作り込む

## 開発上の注意

- 単発の巨大リサーチ（1,000本規模）はいきなりやらず、検証フェーズを経てから着手する
- 税務: ドル建て報酬は円換算して確定申告が必要（金額次第で税理士相談も検討）

## セットアップ

```bash
cp .env.example .env
# .env にPinterest API v5の認証情報等を記入
```
